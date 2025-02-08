Simple Network Management Protocol (SNMP) is an application–layer protocol defined by the Internet Architecture Board (IAB) in RFC1157 for exchanging management information between network devices.

# SNMP Manager:
- A manager or management system is a separate entity that is responsible to communicate with the SNMP agent implemented network devices. This is typically a computer that is used to run one or more network management systems.

SNMP Manager’s key functions
- Queries agents
- Gets responses from agents
- Sets variables in agents
- Acknowledges asynchronous events from agents

# SNMP Agent:
- The agent is a program that is packaged within the network element. Enabling the agent allows it to collect the management information database from the device locally and makes it available to the SNMP manager, when it is queried for. These agents could be standard (e.g. Net-SNMP) or specific to a vendor (e.g. HP insight agent)

# SNMP agent’s key functions
- Collects management information about its local environment
- Stores and retrieves management information as defined in the MIB.
- Signals an event to the manager.
- Acts as a proxy for some non–SNMP manageable network node.

# Management Information database or Management Information Base (MIB)
- Every SNMP agent maintains an information database describing the managed device parameters. The SNMP manager uses this database to request the agent for specific information and further translates the information as needed for the Network Management System (NMS). This commonly shared database between the Agent and the Manager is called Management Information Base (MIB).

- Typically these MIB contains standard set of statistical and control values defined for hardware nodes on a network. SNMP also allows the extension of these standard values with values specific to a particular agent through the use of private MIBs.

- In short, MIB files are the set of questions that a SNMP Manager can ask the agent. Agent collects these data locally and stores it, as defined in the MIB. So, the SNMP Manager should be aware of these standard and private questions for every type of agent.

## There are two types of Managed Object or Object ID: Scalar and Tabular.
- Scalar: Device’s vendor name, the result can be only one. (As definition says: "Scalar Object define a single object instance")

- Tabular: CPU utilization of a Quad Processor, this would give me a result for each CPU separately, means there will be 4 results for that particular Object ID. (As definition says: "Tabular object defines multiple related object instance that are grouped together in MIB tables")

- In practice this means that every OID you will deal with will either
begin with .1.3.6.1.2 (the standard Management OIDs, that are
vendor neutral); or .1.3.6.1.4.1 (the private OIDs. Each vendor can
be assigned their own private number below .4.1, and then manage
their own OID objects below this. Cisco Systems was allocated .9 -
thus all Cisco Systems OIDs, for information they want to return that
is specific to Cisco equipment, is under .1.3.6.1.4.1.9.) 





- The definition of what information should be made available by the Agent, and requested by the Manager, goes in a MIB. A MIB is the "glue", a directory of what sort of things any particular system can/should offer. It maps numeric codes to names and types that allow us to make sense of the data, much like how a phone directory maps phone numbers to people's names and addresses.