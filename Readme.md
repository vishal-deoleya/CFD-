B-Vote - Microsoft Code-Fun-Do Project
Voting is one of the most significant aspects of any organization or country. Through this project, our team aims to solve the problems underlying the traditional voting systems using innovations from the blockchain ecosystem and building a prototype on the Microsoft azure blockchain platform.

Description of Idea
Innovations have always replaced the older for good, disruption of various industries by blockchain technology is no exception to this. Traditionally existing voting techniques often come under scrutiny because of multiple inefficiencies, be it EVM hacking accusations or booth capturing. What if this blockchain innovation gives a solution to all these problems? Well, with this app, we aim to provide an innovative solution to all these problems.

Through this application, we wish to implement the following:

A voting system which does not depend on a centralized party for ballot tallying and result publishing.
Voting system where voters can vote from anywhere in the world.
Voting system which guarantees confidentiality of the votes cast.
Voting system which ensures the correct counting of votes as long as a majority of the nodes are not corrupt and the result can be published moments after the votes are cast.
A platform-independent secure and verifiable voting system that can be deployed on any blockchain that supports the execution of a smart contract.
The users will be able to log in to the app or create a new voter id when they turned 18 using their currently existing aadhar or DL, the validation of these will be done simultaneously, and if all goes well, the user will be able to login into the app. But here, to cast a vote user will be required to provide his/her fingerprint. The fingerprint will be used to generate a unique hash user using fuzzy extractors. This hash will further be rehashed along with a nonce developed by our algorithm, which will add a layer to users anonymity. The final hash will be used to sign the transaction(vote), and because it is based on users fingerprint, one will be able to cast a vote on behalf of others and also enables the user to remain anonymous. If this particular hash has not been used before, the vote goes through the consensus policy(BFT by default), and the world state is updated. The application then updates the current election standings. Finally, when voting time is over, and all votes have been recorded on the blockchain, it becomes immutable. Furthermore, a smart contract can be developed to automate tallying of the votes. Thus voting via blockchain becomes a cost-efficient, secure, and transparent process which not only eliminates election fraud but also makes voting easy for the common man.
