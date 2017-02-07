# DistributedNetworkAlgorithms

		Distributed network algorithms 

Implementation and virtualization of algorithms on syncronous and asynchronous distributed network topologies

<b>K election leader on one direction network with n nodes.</b>
Algorithm Description:
Every node holds a vector of k elements.
First round: Every node sends its id to the next and adds ths received id in the vector.
Second round: Every node sends the id that received at the first round to the next and 
	adds the received id in the vector and sorts the vector.
ith round: Every node sends the id that received at the i-1th round to its next, compares the id 
	with the elements of the vector, if there are elements with smaller value, the id is added
	in the vector's appropriate position and the smallest element is removed. 
nth round: Every node holds a k-element vector of the ids sortened, so if its id exists in the vector, the node
	is one of the k leaders.

folder: /k-election_leader

HOW TO RUN:
1)Open the server.html file in browser (preferred Firefox). 
2)Then open 8 client.html in the browser.



<b>Leader election with HS algorithm on syncrhonous faultless ring network</b>
HS Algorithm Description:
https://en.wikipedia.org/wiki/HS_algorithm

folder: /Hs_on_ring_network/HS_faultless

Leader election with HS algorithm on synchronous ring network with p possibility of failure
Send every message 1/p times. Every node sends the same number of successful messages it receives.

folder: /Hs_on_ring_network/HS_p_failure

HOW TO RUN:
1)Open the server.html file in browser (preferred Firefox). 
2)Then open 8 client.html files in the browser.


<b>Two face commit</b>
Description algorithm:

Commit request phase
    1)The coordinator sends a query to commit message to all cohorts and waits until it has received a reply from all cohorts.
    2)The cohorts execute the transaction up to the point where they will be asked to commit. They each write an entry to their undo log and an entry to their redo log.
    3)Each cohort replies with an agreement message (cohort votes Yes to commit), if the cohort's actions succeeded, or an abort message (cohort votes No, not to commit), if the cohort experiences a failure that will make it impossible to commit.

Commit phase
Success (If the coordinator received an agreement message from all cohorts during the commit-request phase):
    1)The coordinator sends a commit message to all the cohorts.
    2)Each cohort completes the operation, and releases all the locks and resources held during the transaction.
    3)Each cohort sends an acknowledgment to the coordinator.
    4)The coordinator completes the transaction when all acknowledgments have been received.

Failure (If any cohort votes No during the commit-request phase (or the coordinator's timeout expires):
    1)The coordinator sends a rollback message to all the cohorts.
    2)Each cohort undoes the transaction using the undo log, and releases the resources and locks held during the transaction.
    3)Each cohort sends an acknowledgement to the coordinator.
    4)The coordinator undoes the transaction when all acknowledgements have been received.

folder: /Two-face_commit

HOW TO RUN:
1)Open the u_0.html file in browser (preferred Firefox). 
2)Then open u_i.html files in the browser.



<b>Mutual exclusion algorithm</b>
Coordinator node:
	Receives requests from the rest nodes for the use of "critical" source. If the source is available sends reply.
	If not places the request in a fifo queue. If the queue is empty coordinator awaits new requests.
Simple nodes:
	Send aknowledgement message to the coordinator and they receive their unique id. Then request message is beeing send.
	When they receive a reply from the coordinator they use the source and send a relaese mesage to the coordinator when
	they release the source.

folder: /mutual_exclusion

HOW TO RUN:
1)Open the u_0.html file in browser (preferred Firefox). 
2)Then open u_i.html files in the browser.


<b>Vector sending coordination on asyncronous network custom algorithm</b>
Coordinator node:
	Receives requests from rest nodes in order to send their vector elements. If it is not receiving the elements of a vector
	it replies to the first node that send request. If it is receiving the elements of a vector, coordinator stores 
	the requests in a fifo queue in order to serve them later.
Simple nodes:
	First they send aknowledgement to the coordinator to receive a unique id. Then they send request message, if they receive a 
	reply they send their vector's elements and after the last element a release message is being sent to the coordinator.

folder: /vector_sending_coordination

HOW TO RUN:
1)Open the server.html file in browser (preferred Firefox). 
2)Then open 8 client.html files in the browser.
