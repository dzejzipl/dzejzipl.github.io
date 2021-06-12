---
title: "Configure Lobby Meeting options in Microsoft Teams"
categories:
    - Microsoft Teams
tags:
    - Lobby
    - Meetings

header-img: "/assets/images/posts/2021/TeamsLobby/top.jpg"
subtitle:   "Configure Lobby Meeting options in Microsoft Teams"
---
![Configure Lobby Meeting options in Microsoft Teams](/assets/images/posts/2021/TeamsLobby/top.jpg)

The last time I have teams meeting on my private tenant and I had issues with the lobby. The default configuration didn't allow me to bypass the lobby and start the meeting. Why? I was interested in that case and I started an investigation on how to configure lobby on Microsoft Teams.

To configure policies in Microsoft Teams, you need to visit [Microsoft Teams Admin Center](https://admin.teams.microsoft.com/dashboard) and go to Meeting > Meetings Policies. On this page, you can find multiple settings, which you can configure and after that - assign to a proper group of users / direct to users. The preferred way is assigning to the group of users because you had control over what user-specific policy is assigned.

![Configure Lobby Meeting options in Microsoft Teams](/assets/images/posts/2021/TeamsLobby/01.png)

The first thing is to create a policy and configure necessary options. You need to provide a name and description. Be careful here, if you have multiple policies you can get lost in policies if you don't create a proper name of policies.

Things, which you want to configure about a lobby you can find in the bottom section of the page.

![Configure Lobby Meeting options in Microsoft Teams](/assets/images/posts/2021/TeamsLobby/02.png)

You need to configure the option named *Automatically admin people*. In my case, I configured it to *People in my organization*. Every other person needs to be accepted before joining the meeting.

![Configure Lobby Meeting options in Microsoft Teams](/assets/images/posts/2021/TeamsLobby/03.png)

When you configure necessary options, you need to assign them to a proper group of users. To do this, go to *Group policy assignment* and click Add Group button.

On the right side, you need to provide a name of the group to which you want to assign the policy, select a rank number (about this you can [read it more here](https://docs.microsoft.com/en-US/microsoftteams/assign-policies#group-assignment-ranking)) and select a proper policy.

![Configure Lobby Meeting options in Microsoft Teams](/assets/images/posts/2021/TeamsLobby/04.png)

So I configured to bypass lobby for Organization only and invited my account from another tenant, after that, I received information that Jakub Piesik is waiting in the lobby and can / cannot join the meeting.

![Configure Lobby Meeting options in Microsoft Teams](/assets/images/posts/2021/TeamsLobby/05.png)

Also, you can configure any other settings if you want for your users.

Credits of photo: [Andrea Piacquadio](https://www.pexels.com/photo/confused-businessman-checking-time-on-wristwatch-3760810/)
