# The Work Loop

We can describe the activity of the organization as a "work loop", something like the "game loop" that drives behavior as long as a computer game is running.

As an IS Specialist, you should expect the work loop to generate certain events that you must handle. Here is a rough sketch of the most common events and the general approach to handle them.

```
handleProductionOutage()	// triggered when a production system is down
	// this takes highest priority, but details need to be defined
	
handleMeetings()	// triggered each day that the team meets
	participate in standup meeting for ops
	for each active project where you are assigned an open GitHub Issue
		participate in standup meeting for project

handleWorkTime()	// triggered whenever you find time to add value
	while you have an open GitHub Issue assigned to you
  		work on the Issue for one pomodoro cycle
        post Issue comment: 1 pomodoro worked, describe progress 
        if you have more time to work
        	take a pomodoro break
            jump to top of loop
        else
        	stop
        	
	findIssuesToBidOn("bug") // bugs are higher priority than new features
	
	if you have no Issue assigned to you
		findIssuesToBidOn("help wanted")
     
findIssuesToBidOn(label)	// a helper process called from handleWorkTime()
	while there are open GitHub Issues marked with label
		choose one and bid (post comment that @mentions manager: I propose to work on this)
     	meet with the manager _in person_
     	if manager assigns Issue to you
     		post comments as needed to cancel other unaccepted bids
     		return
```

Keep in mind that this is a rough sketch-- guidelines. It is impossible to reduce good knowledge workers to an algorithm, and it may be unethical to try. There is still plenty of need for good judgment. For example:

- You might get to the end of the `handleWorkTime()` process sketched above, but still have no open Issue assigned to you. You would need to use your judgment about how best to create value.
- In the `findIssuesToBidOn()` process, the manager may be proactive and assign the Issue to you before you meet in person. That's fine, but otherwise it is *your* responsibility to meet them in person; otherwise you are creating subordinate-imposed time and the monkey is on the wrong back.
- A manager may have multiple people bidding to work the same Issue. Your history of good judgment is one thing that might be considered when choosing who to assign.









```
while you are a member of this organization
	while you have an open GitHub Issue assigned to you
		work toward closing the assigned Issue
		post comment to describe your progress and time worked
		
	findIssuesToBidOn("bug") // bugs are higher priority than new features
	
	if you have no Issue assigned to you
		findIssuesToBidOn("help wanted")
		
		
	
findIssuesToBidOn(label)	
	while there are open GitHub Issues marked with label
		choose one and bid (post a comment that @mentions manager: I propose to work on this)
		meet with the manager
		if manager assigns Issue to you
			post comments as needed to cancel other unaccepted bids
			return

```



