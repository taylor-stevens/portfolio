<template>
    <v-container class="fill-height">
        <v-row>
            <v-col>
                <div class="text-h4" style="margin-top: 3%; margin-bottom: 3%;">
                    Implementation of the "Friends Feature" within the Covey.Town World
                </div>
                <div style="margin-bottom: 3%;">
                All of the infomation found in this tab is referenced from the Implementation Report for this project.
                <br><br>
                The primary feature that our team added to Covey.Town is Friends functionality: allowing players to 
                become friends with each other. Once two players are friends, they can take advantage of the features 
                we added that are offered exclusively for players with friends: teleporting, sending MiniMessages, and 
                sending ConversationArea invites (herein collectively defined as “extended Friends features”). Initially, 
                each player will see every other player in the town under the “Other Players In This Town” heading on the 
                Social Sidebar. When a player gains a friend, the friend’s name is instead displayed under the “Friends” 
                heading.
                The current repository can be found
                <a
                    key="Github"
                    href="https://github.com/neu-cs4530/covey-town-friends-feature"
                    title="Github"
                    class="d-inline-block mx-2 social-link"
                    rel="noopener noreferrer"
                    target="_blank"
                >
                    <v-icon
                    :icon="'fa-brands fa-github'"
                    size="24"
                    style="color: white;"
                    />
                </a>
                <a href="https://github.com/neu-cs4530/covey-town-friends-feature" target="_blank">here</a>. The original
                site was being run on <a href="https://covey-town-with-friends-group-308.netlify.app/" target="_blank">this netlify site</a>.
            </div>
            </v-col>
        </v-row>
        <v-row justify-self="center" justify="center" style="margin-bottom: 3%;">
            <v-col>
                <v-img src="./coveytown.png"
                justify-self="center"
                >
                </v-img>
            </v-col>
            <v-col cols="1">
                <v-container class="grow d-flex flex-column flex-nowrap">
                    <v-row style="padding-bottom: 10%;">
                        <v-icon
                        :icon="'fa-brands fa-react'"
                        size="50"
                        style="color: white;"
                        />
                    </v-row>
                    <v-row style="padding-bottom: 10%;">
                        <v-img src="../assets/jest.png"></v-img>
                    </v-row>
                    <v-row style="padding-bottom: 10%;">
                        <v-icon
                        :icon="'fa-brands fa-sass'"
                        size="50"
                        style="color: white;"
                        />
                    </v-row>
                    <v-row style="padding-bottom: 10%;">
                        <v-img src="../assets/language-typescript.png"></v-img>
                    </v-row>
                    <v-row style="padding-bottom: 10%;">
                        <v-icon
                        :icon="'fa-brands fa-css3'"
                        size="50"
                        style="color: white;"
                        />
                    </v-row>
                    <v-row style="padding-bottom: 10%;">
                        <v-icon
                        :icon="'fa-brands fa-html5'"
                        size="50"
                        style="color: white;"
                        />
                    </v-row>
                </v-container>
            </v-col>
        </v-row>
        <v-row>
            <v-col>
                <div class="text-h5">
                    Technical Overview
                </div>
                <br>
                Most of the substantive changes to the existing Covey.Town codebase were made in Town.ts and TownController.ts.
                This is in part due to the main functionality of our features involving the addition of communication lines 
                between players (i.e., TownControllers) in a given Town. To create these lines of communication, we closely 
                paralleled the structure used for various events, such as interactableUpdate, prevalent in Individual Project 
                1 & 2. 
                <br><br>
                We started by adding new client-to-socket and socket-to-client events in CoveyTownSocket.ts, as well as new 
                object types for these events to share information between the frontend and backend. We chose to prioritize 
                reduction of transported data by sending only necessary information as opposed to reusing a singular broad 
                event type. This design choice is reflected in our decision to create both a ConversationAreaGroupInvite and 
                a TeleportInviteSingular object type.
                <br><br>
                Once these were created, the bulk of the work was spent creating methods in Town.ts and TownController.ts to emit 
                these events, and listeners in both of these classes to catch them. In TownController, we created methods 
                corresponding to interactions a user could have in Covey.Town (such as sending a friend request), each of which 
                emit corresponding client-to-server events (ex: sendFriendRequest) to the shared backend (Town.ts). In Town, we 
                registered client-to-server event listeners under the addPlayer() method. The majority of these listeners call a 
                corresponding Town method, which modifies backend data based on the provided information and then emits an equivalent 
                socket-to-client event. In TownController, we registered listeners for these socket-to-client events under the 
                registerSocketListeners() method, completing the frontend-backend-frontend loop. It should be noted that some of 
                the listeners registered in Town.ts only emit the socket-to-client events, without actually performing backend 
                changes. These events correspond to user actions that modify the user interfaces of at least two players without 
                affecting any backend data (e.g., sending a friend request). Since TownControllers don’t have built-in direct 
                communication with each other, going through the backend for these types of actions ensures that the socket-to-client 
                events will be received by all players in the Town, and thus that all players involved in said action can 
                propagate updates to their interfaces accordingly.
                <br><br>
                The primary function of the listeners registered in TownController is to verify that the received event concerns said 
                TownController’s user, and if it does, use the provided information to update one of four states: the TownController’s 
                friends list, the TownController’s selected friends list, the TownController’s friend requests list, or the 
                TownController’s conversation area invites list. The setters for each of these four states all emit a unique 
                parameter-changed event, which is then caught by a corresponding React hook (defined in TownController.ts) to 
                re-render the parameter. These hooks are then used in the frontend files to update the UI accordingly. The MiniMessage 
                line of communication is implemented slightly differently, in that we didn’t create a parameter to update in 
                TownController.ts - we simply emit a newMiniMessageReceived event in our listener for the miniMessageSent event. 
                This event is then caught in the frontend (TownMap.tsx), along with the associated necessary information, to
                render the appropriate toast message on the corresponding players’ screen.
                <br><br>
                Most of our changes to the UI involved modifying the Social Sidebar. It now first displays a list of the 
                user’s friends, with associated teleport-to and unfriend buttons, followed by a button to invite selected 
                friends to a conversation area, and a text box to write and send short messages (MiniMessages) to selected 
                friends. In the next section, which displays the non-friends list (previously the town occupants list), 
                users can now act via buttons to send, cancel, accept, or decline friend requests to other Town occupants. 
                Additionally, with the help of a button in the active conversation areas section, a user can open a Chakra 
                Drawer displaying all received conversation area invites, with the ability to accept or decline them. 
                As another design choice, part of our refactoring involved modifying and renaming the PlayersList file to 
                NonFriendsListArea, to prevent redundancy between the FriendsList we’d be displaying and the list of remaining 
                players in the Town (ensuring mutual exclusivity between players and friends). Finally, App.css, ChatWindow.tsx, 
                ParticipantList.tsx, and Room.tsx were also slightly modified in order to make the Social Sidebar respond to 
                mouse events, and wrap the video area overlay so it wouldn't obscure any of our added features.
            </v-col>
            <v-col>
                <div class="text-h5">
                    Process Overview
                </div>
                <br>
                Using AGILE methodology, our group modeled a SCRUM team implementing a Kanban board on JIRA. We established 
                early on the general process that we wanted to follow via weekly two-hour planning meetings, and revised 
                this process throughout the project. For each meeting, we began with a quick stand-up to communicate 
                progress statuses. The latter portions of the meetings were dedicated to collaborative work, such as 
                completing reviews on outstanding pull requests (PRs), co-programming to help each other with any blockers 
                regarding coding issues (such as failing tests, trouble implementing design, or difficulty with requirements), 
                as well as doing planning and re-evaluation for the next sprint.
                <br><br>
                We began with writing a Project Plan, in which we described and drafted visuals for our feature, identified 
                user stories and conditions of satisfaction, and created an initial list outlining tasks to complete. 
                These tasks started out relatively vague and incomplete as we did not have a great understanding of the 
                codebase at that time. The initial high-level tasks were then added to the JIRA board, and revised as more 
                detailed planning occurred each sprint to include specific requirements. Each task had a “lead” and a backup 
                programmer assigned to them. These assignments were also re-evaluated during our weekly meetings based on 
                newly acquired knowledge and team members’ preferences for different tasks.
                <br><br>
                Our weekly meeting took place the day after each sprint ended (Thursday), so they were used as informal 
                sprint retrospectives. We focused on clarifying and redefining the tasks for the coming sprint at these 
                meetings, as well as assigning team members to those tasks. We also discussed any other non-task related 
                items that we wanted to change for the next sprint. One main point of discussion was our Git branching 
                strategy. The key factor of our branching strategy was the creation of a development branch (“dev” branch). 
                For each sprint, we created a new dev branch off of main from which everyone was required to create their 
                task branches off of. PRs and reviews therefore branched off of the dev branch, which granted us another 
                level of separation between the code that was fit for deployment (main) and code that contained new features 
                but hadn’t yet been cleared for deployment (dev branch). Before asking for reviews, we required PRs to come 
                with detailed descriptions and passing tests. In order to merge a PR, at least two reviews were required. 
                Often, we waited for all 3 reviews to ensure that all sprint members were seeing the code that was being 
                added. In specific cases, where only a few lines had been edited, or two reviews were not possible in the 
                desired timeframe, one reviewer was deemed sufficient. When PRs were opened outside of meeting times, 
                asynchronous reviews were requested to increase review efficiency. In the asynchronous reviews, the PR 
                creator gave an overview of decisions they made, either in the PR description or by adding Github comments 
                on any relevant lines. We practiced blameless reviews, making sure to never discourage or blame anyone for 
                decisions that we disagreed with or thought were suboptimal. It was very important to our group that we 
                justified and discussed any non-trivial project decisions.
                <br><br>
                In addition to discussing via PRs, our main method of communication was a text group chat. We used this chat 
                to ping each other about scheduling, planning, PRs, reviews, and as a medium to hold more extensive and 
                complicated discussions and decisions – which aren’t convenient on Github. 
                <br><br>
                To give more detail to our Kanban board process, we had a 5-column board with the following headings: 
                Backlog, Next Sprint, In Progress, Group Review, and Completed. The headings are mostly self explanatory, 
                but in Backlog we had the tasks that were initially defined, but not revised or ready for the current sprint. 
                We also defined here any tasks that we could revisit if there was extra time - primarily refactoring tasks. 
                Tasks were put into the Next Sprint section once they were discussed during our weekly meetings (and the 
                corresponding task cards were rewritten to be more detailed). JIRA also allowed us to assign people 
                specifically to tasks, which allowed us to conveniently organize and track task leads.
                <br><br>
                As for the sprints, there were 4 sprints (0 through 3) defined for all groups, which we adjusted slightly. 
                All sprints were scheduled to be two weeks, except for Sprint 1. Our team had mistakenly planned for the 
                one-week sprint being Sprint 2, meaning we assigned approximately twice as many tasks for Sprint 1 and half 
                as many for Sprint 2 than would be assigned with the intended durations. We reconciled this issue by keeping 
                Sprint 1 as-is, but by creating ‘Sprint 1.5’ to bridge the differences of our duration breakdowns. Sprint 1 
                initially had eight tasks (two per person), which made it easy to divide it into two separate sprints.
            </v-col>
        </v-row>
    </v-container>
</template>

<script>
//
</script>