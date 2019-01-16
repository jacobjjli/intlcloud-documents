1. Open [Tencent Cloud Direct Connect Console - Dedicated Tunnel](https://console.cloud.tencent.com/vpc/dcConn);
2. Click **+ New** to initiate the application for Dedicated Tunnel. You need to enter the following information to create a Dedicated Tunnel:
<style>
table th:first-of-type {
    width: 150px;
}
</style>

| Parameter | Description | Remarks |
| --------- | -------------------------------- | -------- |
| Dedicated Tunnel name | Create your Dedicated Tunnel name |      -     |
| Connection Type | My Connection, which is the Connection under your account, and shared Connection, which is the Connection connecting other accounts |    -       |
| Provider Account ID | Enter the account under which the Connection is to be shared | Only valid for shared Connection |
| Connection ID | Select the ID of the Connection for which you want to setup a tunnel |       -    |
| Connection ID | Enter the ID of the Connection for which you want to setup a tunnel | Only valid for shared Direct Connect |
| Access network | VPC and BM network are supported |        -   |
| VPC/BM network | Select the ID of the network accessed via the Dedicated Tunnel |       -    |
| Direct Connect gateway | The gateway type is displayed on the left of the gateway name. Check if it meets you need |    -       |
| VLANID      | Enter the non-conflicted VLANID, which cannot be 0 in the mode of "shared Direct Connect", 0 indicates that the sub-API is not enabled for the Connection and only one tunnel can be created | VLANID of the API via which Connection and Tencent Cloud are interconnected |
| Interconnection method | Support auto assignment and manual assignment. If manual assignment is selected, pay attention to the accuracy of the interconnection IP | The interconnection IP cannot be changed after submission |
| Routing method | Support BPG route and static route. Routing information is required for static route | If static route is selected, ip-sla is not supported. Use BFD for BGP |
| BGP ASN   | Optional, automatically assigned if not specified. If the private ASN is out of range, use Fake ASN technology to solve it |     -      |
| BGP key | Optional, "Tencent" is displayed at frontend by default. Default is "Tencent". The key is not needed if it is left empty |     -      |
| Peer IP address range | Enter the user's IDC IP address range, which cannot conflict with that of VPC except in NAT mode | Only valid for static route |  

>**Note:**
- Only one Dedicated Tunnel can be created if the sub-API is not enabled for the Connection. To create more tunnels, enable the sub-API mode for the network topology that created multiple tunnels and connected multiple VPCs.
Reason: The billed traffic of the Dedicated Tunnel comes from the sub-API of the Connection. If you create local, cross-city, or even cross-country tunnel interconnection without enabling sub-API, it is technically impossible to distinguish the traffic of different tunnels. In such case, the traffic consumed by the Connection API is billed based on the standard for cross-country interconnection and the originally free traffic consumed by local interconnection will also be billed.
If you want to create more tunnels or change the configuration, contact your Direct Connect manager.
- To ensure the refined scheduling capability of your network, do not publish the following routes: 10.0.0.0/8, 172.16.0.0/12, 192.168.0.0/16 and 100.64.0.0/10.

#### How do you know the progress of tunnel construction?
- After submitting the application for the Dedicated Tunnel, the configuration of devices on the cloud is distributed immediately. It is recommended that you first configure the interconnection IP of devices not on the cloud to avoid the loss of associated tunnel traffic.
- You can see the progress of tunnel construction in the "Connection Status" under the Dedicated Tunnel. If the status of "Configuring" remains unchanged for more than 30 minutes, the tunnel application has been submitted to customer service for processing for security reasons. Please contact your architect or after-sales manager to follow up.
