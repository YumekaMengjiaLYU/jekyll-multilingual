---
layout: post
title:  "Model-Free Prediction"
ref: welcome
date:   2020-07-14
tags: reinforcement-learning-lectures
lang: en
---

Application layer
presentation layer
session layer
transport layer
network layer
data link layer
physical layer

All people seem to need data processing.
Please do not throw sausage pizza away.

- Abtract model

- Set of specifically created protocols

- Protocols not used in any network system

### Layer 1: Physical layer
- Bottome layer

- Concerned with physical transmission of raw data

- Transmits data in the form of 1s and 0s

- Defines encoding methods to transmit data

- Defines how bits are placed on media

- Defines how to know when bits start and stop

- Defines specifications for media usage

- Define kinds of media permitted

- Defines how physical connections are made

- Defines pin usage in physical connections

- Specifies standards that apply to specific types of media

### Layer 2: Data Link Layer

- Provides error-free transmission from one node to the next over physical media

- Establishes and terminates links between nodes

- Responsible for traffic control

- Transmits and receives frames sequentially

- Responsible for frame acknowledgement

- Provides and expects frame acknowledgement

- Detects and recovers from errors on physical layer

- Retransmits nonacknowledged frames

- Handles duplicate frame receipt

- Responsible for frame delimiting

- Creates and recognizes frame boundaries

- Responsible for error checking

- Checks received frames for data integrity

- Provides media access management - determine when node is allowed to use physical media

### Layer 3: Network Layer
- Controls the operations of the subnetwork it is on

- Determines best physical path for data

- Uses network conditions to choose best path

- Uses priority of service to determine best path

- Uses other factors to determine best path

#### Functions it provides

- Routing
    - Routes frames among connected networks

- Subnet traffic control
    - Allows routers to send instructions to sending nodes to "throttle back" frame transimissions when buffles are filled

- Frame fragmentation
    - Determines frame size of routers located down stream

    - Frame size called maximum transimission unit size

- Logical-physical address mapping

    - Translates logical addresses into physical addresses

- Subnet usage accounting

    - Has function that allows device to keep track of frames forwarded by subnet intermediate systems

    - Uses this to produce billing information

#### Communications Subnets

- Build headers used by network layer on other devices to route packets to destination

- Relieve higher layers of the need-to-know data transmission and switching technologies

- Use protocols on lower layers to send data to destinations separated by intermediate nodes

- Send information between adjacent nodes

### Transport Layer

- Ensures messages delivered error-free

- Ensures messages delivered in sequence

- Ensures messages delivered with no loss or duplication

- Relieves higher protocols of concern for transfer of data

- Size and complexity of transport protocols dependent on service provided by network

#### Segmentation

- Accepts messages from session layer

- Splits message into smaller units

- Imposes message size limits on network layer protocols

- Prepares header for each smaller units created

- Passes smaller uints to network layer

- Reassemble message at destination

- Header for smaller units contain certain elements

    - Header contains start and end flags

    - contains sequence information

- Message acknowledgement


    - Provides reliable end-to-end delivery of messages

    - End-to-end delivery accompanied by acknowledgements

- Message traffic control

    - Controls rate of traffic sent when no buffers available

- Session  multiplexing

    - Breaks all the data coming in on one link into separate data streams

    - Those data streams are called sessions

    - Tracks which message belongs to which session

#### End-to-End layers

- Transport layer and above layers not responsible for transmission between nodes

- Transport and above layers responsible for source to destination transmission

- Source-to-destination transmissions also called end-to-end communications

- Upper layers not concerned with underlying communications facility

### Session Layer

- Responsible for establishing sessions between processes running on different computers

- Provides several functions to accomplish this

- Session establishment, maintenance, and termination

- Session support

#### Maintenance Termination

- Allows application processes on different machines to do several things between the machines

- Allows processes to establish a connection

- Allows processes to use a connection

- Allows processes to terminate a connection

#### Session support

- Performs the function of allowing processes to communicate over network

- Performs security

- Performs name recognition

- Performs logging on

- Performs other functions that are less common

### Presentation Layer

- Formats data to be presented to the application layer

- Translator for the network

- At sending station translates data from application layer format to common format recognized by across networks

- At receiving station translates data from common format to format used by application layer
## TCP/IP

TCP - Transport Control Protocol

IP - Internet Protocol

- It is the protocol used by the Internet!

### Application

### Transport

### Internet

### Link layer