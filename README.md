# LICS-Project
Title: Formal Modeling and Verification of a Library System using UPPAAL

Abstract:

This document presents a detailed model of a library-based system using the UPPAAL model checker. The system comprises three templates: User, Bank, and Library, each contributing to a seamless user experience in buying gold or platinum cards and viewing transaction history. The UPPAAL model checker is employed to verify the system's correctness and adherence to specified properties.

1.⁠ ⁠Introduction:

The library-based system is designed to offer users the ability to buy gold or platinum cards and view their transaction history. The system's formal representation involves three main components: User, Bank, and Library. Each template interacts with others through channels and broadcast channels, ensuring synchronized execution.

2.⁠ ⁠System Initialization:

The initial states of the system are defined as follows:

User: LogOut
Bank: Idle
Library: Idle
Channels facilitate synchronization between User and Bank, and broadcast channels extend this synchronization to all three templates.

3.⁠ ⁠User Interaction:

Upon initiating a sign-in, the User template signals the Library. Upon a successful sign-in, the User transitions to the Authenticated state, where two options are presented: view history or buy membership. Following the history display, the user promptly logs out.

4.⁠ ⁠Buy Membership Process:

Upon choosing to buy a membership, the Bank transitions from Idle to the Call Bank state. Broadcast channels are utilized for selecting gold or platinum memberships. The credit card and debit card options trigger further actions:

Credit Card Option: The user is guaranteed success, assuming availability of a credit card, as the system assumes the ability to withdraw money without checking the bank balance.

Debit Card Option: The Bank checks the user's bank balance based on the chosen gold or platinum option. If the balance is sufficient, success is set to true, and the transaction proceeds. Otherwise, success is maintained at its current state, and the paysuccess variable is selected.

5.⁠ ⁠The Success Variable:

The success variable plays a crucial role in determining the outcome of the transaction. Its value is contingent on the chosen membership type and the user's bank balance. If the conditions for a successful transaction are met, the success variable is set to true, indicating a positive outcome. In cases where the transaction cannot proceed due to insufficient funds, the success variable remains false.
