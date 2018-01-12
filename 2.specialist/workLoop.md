# The Work Loop

We can describe the activity of the organization as a "work loop", something like the "game loop" that drives behavior as long as a computer game is running.

As an IS Specialist, you should expect the work loop to generate certain events that you must handle. Here is a rough sketch of the most common events and the general approach to handle them.

```
handleProductionOutage()	// triggered when a production system is down
    // this takes highest priority, but details need to be defined
	
handleMeetings()	       // triggered each day that the team meets
    participate in standup meeting for ops
    for each active project where you are assigned an open GitHub Issue
        participate in standup meeting for project
    report to manager(s) according to agreed upon degree of initiative

handleWorkTime()	       // triggered whenever you find time to add value
    while you have an open GitHub Issue assigned to you
        work on the Issue for one pomodoro cycle
        post Issue comment: 1 pomodoro worked, describe progress, @mention manager per agreed degree of initiative 
        if you have more time to work
            take a pomodoro break
            jump to top of loop
        else
            stop
        	
findIssuesToBidOn("bug")       // bugs are higher priority than new features
	
if you have no Issue assigned to you
    findIssuesToBidOn("help wanted")
     
findIssuesToBidOn(label)       // a helper process called from handleWorkTime()
    while there are open GitHub Issues marked with label
        choose one and bid (post comment that @mentions manager: I propose to work on this)
        meet with the manager _in person_
        if manager assigns Issue to you (along with reporting time and degree of intitiative)
            post comments as needed to cancel other unaccepted bids
            return
```

Keep in mind that this is a rough sketch-- guidelines. It is impossible to reduce good knowledge workers to an algorithm, and it may be unethical to try. There is still plenty of need for good judgment. For example:

- You might get to the end of the `handleWorkTime()` process sketched above, but still have no open Issue assigned to you. You would need to use your judgment about how best to create value.
- In the `findIssuesToBidOn()` process, you must decide if the `meet with the manager _in person_` step is *blocking*-- that is, how long do you try to meet before you loop around and bid on another Issue? (A manager may be proactive and assign an Issue to you before you meet in person. That's fine, but otherwise it is *your* responsibility to meet them in person; otherwise you are creating subordinate-imposed time and the monkey is on the wrong back.)
- As written, you can only have one open Issue assigned to you at a time. While the number should be *very small*, more than one is okay, especially when it is needed to keep you productively occupied.
- You might also use judgment to keep yourself productively occupied by bidding for work before you get to the point you have nothing to do-- but not *too* soon.
- A manager may have multiple people bidding to work the same Issue. Your history of good judgment is one thing that might be considered when choosing who to assign.
