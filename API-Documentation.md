## Overview
FDMiner offers a comprehensive set of APIs designed for smooth integration with both OEM systems and custom tools. These APIs are utilized by the custom Foundry dashboard to retrieve data from the miner and also by the site engineers to configure miner parameters through scripts or standalone CGI tools.
FDMiner supports two family of APIs (APIs of two types based on the end point to which it is being called to (or from)): <br>
  a. CGMiner <br>
  b. CGI style <br>
CGMiner based APIs are supported to preserve compatibility with other leading Mining Equipment.

***

## CGMiner Commands
FDMiner hosts a TCP server. These commands listen on a simple **TCP/IP socket over the port 4028** for a single string. The FW serves this API by replying with a string and then closes the connection.

**Request:**
These API requests are in simple JSON format as shown below:

	{"command":"CMD","parameter":"PARAM"}

The “command” field is mandatory, the “parameter” field is optional.

**Response: **
The responses received are in simple text format.
Each response of this kind starts with the “Status” section and is followed by the section containing the API response and an “id” section at the end of the response.

The server returns error status if the Request JSON format/parameter is invalid.

<details>
<summary>
<h3> List of Commands <h3>
</summary>

<details>
<summary>
<h4> {"command":"stats"} </h4>

**Description:** Fetch Miner data like Hash Board Temperature, Chip Temperature, Fan Speed, Hash Rate and other essential miner data from server. 

</summary>

**End Point(URL):** tcp://<Miner_ip>:4028

**Parameters:** None

**Response:**

```json
{
  "STATUS": [
    {
      "STATUS": "S",
      "When": 1722944585,
      "Code": 70,
      "Msg": "BCFMiner Stats",
      "Description": "BCFMiner 2.4.M.Fpsu_Test"
    }
  ],
  "STATS": [
    {
      "BMMiner": "2.4.M.Fpsu_Test",
      "Miner": "FCB V3 Rev A Proto",
      "CompileTime": "Tue Jul 30 01:05:32 CST 2024",
      "Type": "Antminer S19JPROWP"
    },
    {
      "STATS": 0,
      "ID": "BTM_SOC0",
      "Elapsed": 4143,
      "Calls": 0,
      "Wait": 0,
      "Max": 0,
      "Min": 99999999,
      "GHS 5s": 90000,
      "GHS av": 89000,
      "rate_30m": 88000,
      "Mode": 2,
      "miner_count": 3,
      "frequency": 477,
      "fan_num": 4,
      "fan1": 5786,
      "fan2": 5732,
      "fan3": 5872,
      "fan4": 5609,
      "temp_num": 3,
      "temp1": 66,
      "temp2_1": 58,
      "temp2": 65,
      "temp2_2": 58,
      "temp3": 66,
      "temp2_3": 58,
      "temp_pcb1": "53-53-61-61",
      "temp_chip1": "58-58-66-66",
      "temp_pic1": "43-43-51-51",
      "temp_pcb2": "53-53-60-60",
      "temp_chip2": "58-58-65-65",
      "temp_pic2": "43-43-50-50",
      "temp_pcb3": "53-53-61-61",
      "temp_chip3": "58-58-66-66",
      "temp_pic3": "43-43-51-51",
      "temp_pcb4": "0-0-0-0",
      "temp_chip4": "0-0-0-0",
      "temp_pic4": "0-0-0-0",
      "total_rateideal": 90000,
      "rate_unit": "GH",
      "total_freqavg": 477,
      "total_acn": 239,
      "total rate": 90.1239776611328,
      "temp_max": 66,
      "no_matching_work": 0,
      "chain_acn1": 79,
      "chain_acn2": 79,
      "chain_acn3": 79,
      "chain_acs1": "ooo ooo ooo ooo ooo ooo ooo ooo ooo ooo ooo ooo ooo ooo ooo ooo ooo ooo ooo ooo ooo ooo ooo ooo ooo ooo ooo ooo ooo ooo ooo ooo ooo ooo ooo ooo ooo ooo ooo ooo ooo ooo",
      "chain_acs2": "ooo ooo ooo ooo ooo ooo ooo ooo ooo ooo ooo ooo ooo ooo ooo ooo ooo ooo ooo ooo ooo ooo ooo ooo ooo ooo ooo ooo ooo ooo ooo ooo ooo ooo ooo ooo ooo ooo ooo ooo ooo ooo",
      "chain_acs3": "ooo ooo ooo ooo ooo ooo ooo ooo ooo ooo ooo ooo ooo ooo ooo ooo ooo ooo ooo ooo ooo ooo ooo ooo ooo ooo ooo ooo ooo ooo ooo ooo ooo ooo ooo ooo ooo ooo ooo ooo ooo ooo",
      "chain_acs4": "",
      "chain_hw1": 1,
      "chain_hw2": 1,
      "chain_hw3": 0,
      "chain_rate1": "29",
      "chain_rate2": "30",
      "chain_rate3": "30",
      "chain_rate4": "",
      "freq1": 477,
      "freq2": 477,
      "freq3": 477,
      "freq4": 0,
      "miner_version": "FCB V3 Rev A Proto",
      "miner_id": "811cc44a6f41a854"
    }
  ],
  "id": 1
}
```
</details>
<details>
<summary>
<h4> {"command":"pools"} </h4>

**Description:**  Fetch Pool Addresses and other essential data of all the pool

</summary>

**End Point(URL):** tcp://<Miner_ip>:4028

**Parameters:** None

**Response:**

```json
{
        "STATUS":       [{
                        "STATUS":       "S",
                        "When": 1719162901,
                        "Code": 7,
                        "Msg":  "3 Pool(s)",
                        "Description":  "BCFMiner 2.4.2 Test2"
                }],
        "POOLS":        [{
                        "POOL": 0,
                        "URL":  "stratum+tcp://btc.foundryusapool.com:3333",
                        "Status":       "Active",
                        "Priority":     0,
                        "Quota":        0,
                        "Getworks":     829,
                        "Accepted":     1760,
                        "Rejected":     3,
                        "Discarded":    0,
                        "Stale":        1,
                        "Get Failures": 0,
                        "Remote Failures":      0,
                        "User": "ccc.S19XP_B1",
                        "Last Share Time":      "1719162878",
                        "Diff": "262K",
                        "Diff1 Shares": 0,
                        "Proxy Type":   "",
                        "Proxy":        "",
                        "Difficulty Accepted":  1872710,
                        "Difficulty Rejected":  0,
                        "Difficulty Stale":     319712,
                        "Last Share Difficulty":        1872710,
                        "Has Stratum":  true,
                        "Stratum Active":       true,
                        "Stratum URL":  "btc.foundryusapool.com",
                        "Has GBT":      false,
                        "Best Share":   173833500
                },
				],
/*Pool2 and Pool 3 Details will also be fetched in the above format*/
/** Response Modified for documentation purpose, Repetitive Data patterns skipped for brief documentation**/

        "id":   1
}

```

> NOTE: <br>
> - Pool2 and Pool 3 Details will also be fetched in the above format <br>
> - Response Modified for documentation purpose, Repetitive Data patterns skipped for precise documentation <br>

</details>

<details>
<summary>

<h4> {"command":"version"} </h4>

**Description:** Fetch API, FDMiner and hardware versions.

</summary>

**End Point(URL):** tcp://<Miner_ip>:4028

**Parameters:** None

**Response:**

```json
{
        "STATUS":       [{
                        "STATUS":       "S",
                        "When": 1719163104,
                        "Code": 22,
                        "Msg":  "BCFMiner Stats",
                        "Description":  "BCFMiner 2.4.2 Test2"
                }],
        "VERSION":      [{
                        "BCFMiner":     "2.4.2 Test2",
                        "API":  "3.1",
                        "Miner":        "FCB V2.2",
                        "CompileTime":  "Wed Jun 12 02:16:32 CST 2024",
                        "Type": "Antminer S19 XP"
                }],
        "id":   1
}
```
</details>

<details>
<summary>

<h4> {"command":"summary"} </h4>

**Description:** Fetch Summary of the Mining Parameters.

</summary>

**End Point(URL):** tcp://<Miner_ip>:4028

**Parameters:** None

**Response:**
```json
{
        "STATUS":       [{
                        "STATUS":       "S",
                        "When": 1719163185,
                        "Code": 11,
                        "Msg":  "Summary",
                        "Description":  "BCFMiner 2.4.2 Test2"
                }],
        "SUMMARY":      [{
                        "Elapsed":      24930,
                        "GHS 5s":       96000,
                        "GHS av":       93000,
                        "GHS 30m":      93000,
                        "Found Blocks": 0,
                        "Getwork":      30,
                        "Accepted":     1787,
                        "Rejected":     3,
                        "Hardware Errors":      6,
                        "Discarded":    56783,
                        "Stale":        3,
                        "Get Failures": 0,
                        "Local Work":   56813,
                        "Remote Failures":      0,
                        "Network Blocks":       1,
                        "Total MH":     96.479156494140625,
                        "Work Utility": 0,
                        "Difficulty Accepted":  262144,
                        "Difficulty Rejected":  262144,
                        "Difficulty Stale":     262144,
                        "Best Share":   262144,
                        "Device Hardware%%":    0,
                        "Device Rejected%%":    0,
                        "Pool Rejected%%":      0,
                        "Pool Stale%%": 0,
                        "Last getwork": 1695624866 }],
        "id":   1}

```
</details>

<details>
<summary>

<h4> {"command":"devs"} </h4>

**Description:** Fetches each available PGA / ASICs data and their details.

</summary>

**End Point(URL):** tcp://<Miner_ip>:4028

**Parameters:** None

**Response:**
```json
{
        "STATUS":       [{
                        "STATUS":       "S",
                        "When": 1719163256,
                        "Code": 9,
                        "Msg":  "1 ASC(s)",
                        "Description":  "BCFMiner 2.4.2 Test2"
                }],
        "DEVS": {
                "":     {
                        "ASC":  0,
                        "Name": "BTM_SOC",
                        "ID":   0,
                        "Enabled":      "Y",
                        "Status":       "Alive",
                        "Temperature":  0,
                        "MHS av":       92000000,
                        "MHS 5s":       92000000,
                        "Accepted":     1791,
                        "Rejected":     1791,
                        "Hardware Errors":      6,
                        "Utility":      0,
                        "Last Share Pool":      0,
                        "Last Share Time":      1695624979,
                        "Total MH":     92000,
                        "Diff1 Work":   262144,
                        "Difficulty Accepted":  262144,
                        "Difficulty Rejected":  262144,
                        "Last Valid Work":      1695624979,
                        "Device Hardware%%":    0,
                        "Device Rejected %%":   0,
                        "Device Elapsed":       25002
                }
        },
        "id":   1
}

```
</details>

<details>
<summary>

<h4> {"command":"prodata"} </h4>

**Description:** Fetches frequency, Health, Hardware errors and Hash Rates of individual ASIC in the miner along with other details.

</summary>

**End Point(URL):** tcp://<Miner_ip>:4028

**Parameters:** None

**Response:**

```json
{
        "STATUS":       [{
                        "STATUS":       "S",
                        "When": 1719163315,
                        "Code": 99,
                        "Msg":  "BCFMiner ProData",
                        "Description":  "BCFMiner 2.4.2 Test2"
                }],
        "PROData":      {
                "Miner Status": "Mining",
                "Miner Name":   "FoundryCBMiner",
                "Voltage":      11.899999618530273,
                "Power": "2.61",
                "Efficiency":   19.38249397277832,
                "FanMode":      0,
                "FanSpeed":     100,
                "manualFanSpeed":       100,
                "HB1State":     1,
                "HB2State":     1,
                "HB3State":     1,
                "asicFreqChain1":       [[320, 320, 320, 320, 320, 320, 320, 320, 320, 320], [320, 320, 320, 320, 320, 320, 320, 320, 320, 320], [320, 320, 320, 320, 320, 320, 320, 320, 320, 320], [320, 320, 320, 320, 320, 320, 320, 320, 320, 320], [320, 320, 320, 320, 320, 320, 320, 320, 320, 320], [320, 320, 320, 320, 320, 320, 320, 320, 320, 320], [320, 320, 320, 320, 320, 320, 320, 320, 320, 320], [320, 320, 320, 320, 320, 320, 320, 320, 320, 320], [320, 320, 320, 320, 320, 320, 320, 320, 320, 320], [320, 320, 320, 320, 320, 320, 320, 320, 320, 320], [320, 320, 320, 320, 320, 320, 320, 320, 320, 320]],
                "asicHRChain1": [[0.27300000190734863, 0.27300000190734863, 0.27300000190734863, 0.27300000190734863, 0.27300000190734863, 0.27300000190734863, 0.27300000190734863, 0.27300000190734863, 0.27300000190734863, 0.27300000190734863], [0.27300000190734863, 0.27300000190734863, 0.27300000190734863, 0.27300000190734863, 0.27300000190734863, 0.27300000190734863, 0.27300000190734863, 0.27300000190734863, 0.27300000190734863, 0.27300000190734863], [0.27300000190734863, 0.27300000190734863, 0.27300000190734863, 0.27300000190734863, 0.27300000190734863, 0.27300000190734863, 0.27300000190734863, 0.27300000190734863, 0.27300000190734863, 0.27300000190734863], [0.27300000190734863, 0.27300000190734863, 0.27300000190734863, 0.27300000190734863, 0.27300000190734863, 0.27300000190734863, 0.27300000190734863, 0.27300000190734863, 0.27300000190734863, 0.27300000190734863], [0.27300000190734863, 0.27300000190734863, 0.27300000190734863, 0.27300000190734863, 0.27300000190734863, 0.27300000190734863, 0.27300000190734863, 0.27300000190734863, 0.27300000190734863, 0.27300000190734863], [0.27300000190734863, 0.27300000190734863, 0.27300000190734863, 0.27300000190734863, 0.27300000190734863, 0.27300000190734863, 0.27300000190734863, 0.27300000190734863, 0.27300000190734863, 0.27300000190734863], [0.27300000190734863, 0.27300000190734863, 0.27300000190734863, 0.27300000190734863, 0.27300000190734863, 0.27300000190734863, 0.27300000190734863, 0.27300000190734863, 0.27300000190734863, 0.27300000190734863], [0.27300000190734863, 0.27300000190734863, 0.27300000190734863, 0.27300000190734863, 0.27300000190734863, 0.27300000190734863, 0.27300000190734863, 0.27300000190734863, 0.27300000190734863, 0.27300000190734863], [0.27300000190734863, 0.27300000190734863, 0.27300000190734863, 0.27300000190734863, 0.27300000190734863, 0.27300000190734863, 0.27300000190734863, 0.27300000190734863, 0.27300000190734863, 0.27300000190734863], [0.27300000190734863, 0.27300000190734863, 0.27300000190734863, 0.27300000190734863, 0.27300000190734863, 0.27300000190734863, 0.27300000190734863, 0.27300000190734863, 0.27300000190734863, 0.27300000190734863], [0.27300000190734863, 0.27300000190734863, 0.27300000190734863, 0.27300000190734863, 0.27300000190734863, 0.27300000190734863, 0.27300000190734863, 0.27300000190734863, 0.27300000190734863, 0.27300000190734863]],
                "asicHWEChain1":        [["-", "-", "-", "-", "-", "-", "-", "-", "-", "-"], ["-", "-", "-", "-", "-", "-", "-", "-", "-", "-"], ["-", "-", "-", "-", "-", "-", "-", "-", "-", "-"], ["-", "-", "-", "-", "-", "-", "-", "-", "-", "-"], ["-", "-", "-", "-", "-", "-", "-", "-", "-", "-"], ["-", "-", "-", "-", "-", "-", "-", "-", "-", "-"], ["-", "-", "-", "-", "-", "-", "-", "-", "-", "-"], ["-", "-", "-", "-", "-", "-", "-", "-", "-", "-"], ["-", "-", "-", "-", "-", "-", "-", "-", "-", "-"], ["-", "-", "-", "-", "-", "-", "-", "-", "-", "-"], ["-", "-", "-", "-", "-", "-", "-", "-", "-", "-"]],
                "asicHealthChain1":     [["-", "-", "-", "-", "-", "-", "-", "-", "-", "-"], ["-", "-", "-", "-", "-", "-", "-", "-", "-", "-"], ["-", "-", "-", "-", "-", "-", "-", "-", "-", "-"], ["-", "-", "-", "-", "-", "-", "-", "-", "-", "-"], ["-", "-", "-", "-", "-", "-", "-", "-", "-", "-"], ["-", "-", "-", "-", "-", "-", "-", "-", "-", "-"], ["-", "-", "-", "-", "-", "-", "-", "-", "-", "-"], ["-", "-", "-", "-", "-", "-", "-", "-", "-", "-"], ["-", "-", "-", "-", "-", "-", "-", "-", "-", "-"], ["-", "-", "-", "-", "-", "-", "-", "-", "-", "-"], ["-", "-", "-", "-", "-", "-", "-", "-", "-", "-"]],
/*"asicFreqChain2" and "asicFreqChain3"  is updated in the same format as above*/
		/*"asicHealthChain2" and "asicHealthChain3"  are updated in the same format as above*/
		/*"asicHRChain2" and "asicHRChain3"  is updated in the same format as above*/
		/*"asicHWEChain2" and "asicHWEChain3"  is updated in the same format as above*/
		/** Response Snipped to keep the document brief**/
                "throttle Mode":        "false",
                "throttleHR":	-1,
		     "throttleFreq":	-1,
                "Miner Mode":   3,
                "Mining Mode":  0,
                "TargetHR":     93,
                "AutoTuneStage":        3,
                "ShutDownTemp": 80,
                "targetChipTemp":       60,
                "maxHrRestartAttempt":	"5",
		     "hrThreshold":	"20",
		     "maxErrRestart":	"5",
		     "minFans":	"4",
                "pool1Port":    3333,
                "pool1PW":      "X",
                "pool2Port":    443,
                "pool2PW":      "X",
                "pool3Port":    25,
                "pool3PW":      "X",
                "Xcord":        "x",
                "Ycord":        "y",
                "Zcord":        "z"
        },
        "id":   1
}

```
</details>

<details>
<summary>

<h4> {"command":"restart"} </h4>

**Description:** This Request restarts the miner.

</summary>

**End Point(URL):** tcp://<Miner_ip>:4028

**Parameters:** None

**Response:** No Response
 
</details>

<details>
<summary>

<h4> {"command":"quit"} </h4>

**Description:** Shuts Down the miner. 

</summary>

**End Point(URL):** tcp://<Miner_ip>:4028

**Parameters:** None

**Response:** No Response

> NOTE: <br>
> - This is a destructive API call. Once the above command is called, the Miner completely shuts down. Only a power cycle will turn on the miner. The user should have physical access to the Machine to turn it back ON. If the machine is connected to a smart PDU, the user can turn it back again over the network using PDU dashboard.
</details>

<details>
<summary>

<h4> {"command":"locate"} </h4>

**Description:** Locates the Miner by Blinking the tower LED continuously and beeping the Buzzer (if connected) for 10 min.
Users can turn off the indication using the toggle switch on the dashboard.

</summary>

**End Point(URL):** tcp://<Miner_ip>:4028

**Parameters:** None

**Response:** No Response

</details>

<details>
<summary>

<h4> {"command":"softExit"} </h4>

**Description:** Gracefully softReboot the miner,by powering off HBs & PSU.Firmware auto restarts after approx. 30 -50 seconds.

</summary>

**End Point(URL):** tcp://<Miner_ip>:4028

**Parameters:** None

**Response:** No Response
 
</details>
</details>

***

## FDMiner Commands
These commands exchange data using **http authentication protocol**,they fetch/send the data from/to the **cgi-bin directory** on the server.

A server using HTTP authentication will respond with a 401 Unauthorized response to a request for a protected resource. This response must include at least one WWW-Authenticate header and at least one challenge, to indicate what authentication schemes can be used to access the resource (Realm Name, Charset, Encryption, etc.

**Request:**
Two Types of requests are used.
**GET** requests-to fetch data from the server’s given endpoint.Input parameters are optional for most of these commands.
**POST** requests- to publish data on  the server’s given endpoint.Parameters Input is Mandatory for these commands.

All the files from which data has to be read or written to are in **<filename>.cgi** format.

**Response:**
Response to all requests are in either JSON or text format.
Server returns code 200 upon successful processing of the request

The server returns the following error codes upon failure to process the request:

- **code 404:** if the requested .cgi file is not found
- **code 400:** if the requested user does not have access privilege
- **code 500:** internal server error.

<details>
<summary>

<h3> GET Commands </h3>

</summary>

<details>
<summary>
<h4> GET getFreeSpace.cgi </h4>

**Description:** Fetches the available free space and other memory details on the Miner controller.

</summary>

**End Point:**/cgi-bin/getFreeSpace.cgi

**Parameters Required:** None

**Response:**

```json
{
  "totalSize": "3698930",
  "usedSpace": "1141956",
  "availableSpace": "2423892",
  "unit": "kb",
  "%used": "30.87",
  "%avail": "65.53"
}

```
**Parameter Specification Table**

----------------------------------------------------------------------------------------------------------------------------------
|Key            | Data-Type|Info|     Valid Values         |  Supported <br> by <br>Foundry FW          |
|---------------|------------------|-----------|-----------|---------------|
|totalSize      |STRING            |Represents the total size of all file systems in kilobytes (KB).|      | Y |
|usedSpace      |STRING            | Represents the total used space of all file systems in kilobytes (KB).|  | Y |
|availableSpace |STRING            | Represents the total available space of all file systems in kilobytes (KB).|    | Y |
|unit           |STRING            |Indicates the unit of measurement for the sizes, which is "kb" (kilobytes).|     | Y |
|%used          |STRING            |Represents the percentage of the total space that is currently used|      | Y |
|%avail         |STRING            |Represents the percentage of the total space that is currently  available|       | Y |                                   


----------------------------------------------------------------------------------------------------------------------------------
</details>

<details>
<summary>

<h4> GET  get_legacy_status.cgi </h4>

**Description:** Legacy status is set to make the miners compatible with foreman tool, when true these miners are supported by foreman.

</summary>
 	
**End Point:**/cgi-bin/get_legacy_status.cgi

**Parameters Required: **

**Response:**
```json
{"legacyStatus":0}

```
</details>

<details>
<summary>
<h4> GET getGraphData.cgi </h4>

**Description:** Fetches the data required for graphical representation of  Hash Rate, Temperature (Inlet and Outlet), and current time.

</summary>

**End Point:** /cgi-bin/getGraphData.cgi

**Parameters Required:** None

**Response:**
```json
{
    "data": [
        {
            "timeDate": "08-07 07:04:32",
            "inletTemp1": "54",
            "inletTemp2": "54",
            "inletTemp3": "54",
            "outletTemp1": "62",
            "outletTemp2": "61",
            "outletTemp3": "61",
            "HB1HR": "29.9",
            "HB2HR": "28.0",
            "HB3HR": "28.7"
        }
    ]
}
```
**Parameter Specification Table**

----------------------------------------------------------------------------------------------------------------------------------
|Key            |               | Data-Type|Info       |  Valid Values |Supported <br>by<br>Foundry FW |
|---------------|---------------|------------------|----------------------------------------------|------|--------------|
|data      |HB1HR          |STRING            |Instantaneous hashrate of Hashboard 1         | |      Y           |
|               |HB2HR          |STRING            |Instantaneous hashrate of Hashboard 2         | |      Y           |
|               |HB3HR          |STRING            |Instantaneous hashrate of Hashboard 3         | |      Y           |
|               |inletTemp1     |STRING            |Hashboard 1 Inlet temp sensor data in °C      | |      Y           |
|               |inletTemp2     |STRING            |Hashboard 2 Inlet temp sensor data in °C      | |      Y           |
|               |inletTemp3     |STRING            |Hashboard 3 Inlet temp sensor data in °C      | |      Y           |
|               |outletTemp1    |STRING            |Hashboard 1 Outlet temp sensor data in °C     | |      Y           |
|               |outletTemp2    |STRING            |Hashboard 2 Outlet temp sensor data in °C     | |      Y           |
|               |outletTemp3    |STRING            |Hashboard 3 Outlet temp sensor data in °C     | |      Y           |
|               |timeDate       |STRING            |Time Stamp when this data was collected in UTC| |      Y           |
----------------------------------------------------------------------------------------------------------------------------------


</details>

<details>
<summary>

<h4> GET get_miner_conf.cgi </h4>

**Description:** Fetches Configuration details of the Miner.

</summary>

**End Point(URL):** /cgi-bin/get_miner_conf.cgi

**Parameters Required:** None

**Response:**
```json
{
"pools" : [
{
"url" : "stratum+tcp://btc.foundryusapool.com:3333",
"user" : "ccc.S19XP_B1",
"pass" : "X"
},
{
"url" : "stratum+tcp://btc.foundryusapool.com:443",
"user" : "ccc.S19XP_B1",
"pass" : "X"
},
{
"url" : "stratum+tcp://btc.foundryusapool.com:25",
"user" : "ccc.S19XP_B1",
"pass" : "X"
}
]
,
"api-listen" : true,
"api-network" : true,
"api-groups" : "A:stats:pools:devs:summary:version",
"api-allow" : "A:0/0,W:*",
"bitmain-fan-ctrl" : true,
"bitmain-fan-pwm" : "10",
"bitmain-use-vil" : true,
"bitmain-freq" : "500",
"bitmain-voltage" : "14",
"bitmain-ccdelay" : "1",
"bitmain-pwth" : "1",
"bitmain-work-mode" : "3",
"bitmain-freq-level" : "70"
}
```
**Parameter Specification Table**

-----------------------------------------------------------------------------------------------------------------------------------------------------------
|Key        |            | Data-Type|Info     |Valid Values                                                  |Supported <br> by <br> FoundryFW|
|-----------|----------------|------------------|----------------|---------------------------------------------------------------|----------------------|
|pools      |url             |STRING            |Pool data in the format stratum+tcp://url:port|                                                               |        Y              |
|           |user            |STRING            |WorkerName      |                                                               |             Y         |
|           |pass            |STRING            |password        |                                                               |            Y          |
|api-listen |                |BOOL              |true.           |                                                               |          Y              |
|api-network|                |BOOL              |true.           |                                                               |     Y                 |
|api-groups |                |STRING            |-               |                                                               |      N                |
|api-allow  |                |STRING            |-               |                                                               |       N               |
|bitmain-fan-ctrl|                |BOOL              |true.           |                                                               |     Y                |
|bitmain-fan-pwm|                |STRING            |-               |                                                               |     N                 |
|bitmain-use-vil|                |BOOL              |true.           |                                                               |       Y               |
|bitmain-freq|                |STRING            |-               |                                                               |       N               |
|bitmain-voltage|                |STRING            |Voltage configured in config file|                                                               |           Y           |
|bitmain-ccdelay|                |STRING            |-               |                                                               |      N                |
|bitmain-pwth|                |STRING            |-               |                                                               |     N                 |
|bitmain-work-mode|                |STRING            |Current work-mode|                                                               |         Y             |
|bitmain-freq-level|                |STRING            |Frequency from config file|                                                               |       Y               |

-----------------------------------------------------------------
</details>

<details>
<summary>

<h4> GET restart.cgi </h4>

**Description:** Restart the Miner.

</summary>

**End Point:** /cgi-bin/restart.cgi

**Parameters Required:** None.

**Response:**
```json
{"STATUS": "BYE"}

```
</details>

<details>
<summary>

<h4> GET get_network_info.cgi </h4>

**Description:** Fetches the network Information

</summary>

**End Point:** /cgi-bin/get_network_info.cgi

**Parameters Required:** None

**Response:**
```json
{
	"nettype": "DHCP",
	"netdevice": "end0",
	"macaddr": "02:03:00:00:00:05",
	"hostname": "foundry-020300000002",
	"ipaddres": "10.2.30.41",
	"netmask": "255.255.255.0",
	"conf_nettype": "DHCP",
	"conf_hostname": "foundry-020300000002",
	"conf_ipaddress": "10.2.30.41",
	"conf_netmask": "255.255.255.0",
	"conf_gateway": "10.2.30.1",
	"conf_dnsservers": "1.1.1.1"
}

```
**Parameter Specification Table**

----------------------------------------------------------------------------------------------------------------------------------
|Key            | Data-Type        |Info       | Valid Values  | Supported <br>by<br>Foundry FW |
|---------------|------------------|-----------|----------------|--------------------------------|
|nettype        |STRING            |DHCP/Static|                |        Y                        |
|netdevice      |STRING            |end0/eth0  |                |         Y                       |
|macaddr        |STRING            |device MAC address ex. 12:34:56:78:9A:BC|                 |       Y          |
|ipaddres       |STRING            |Device IP Address ex. 192.168.0.123|                  |          Y      |
|netmask        |STRING            |Network Mask for the IP ex. 255.255.255.0|           |          Y        |
|conf_nettype   |STRING            |DHCP/Static|              |        Y                  |
|conf_hostname  |STRING            |Current linux username ex. foundry-020150250336|             |      Y       |
|conf_ipaddress |STRING            |Device IP Address ex. 192.168.0.123|        |     Y      |
|conf_netmask   |STRING            |Device IP Address ex. 192.168.0.123|         |     Y        |
|conf_gateway   |STRING            |Device gateway IP Address ex. 192.168.0.1|          |     Y    |
|conf_dnsservers|STRING            |DNS server IP ex. 8.8.8.8|          |         Y     |
----------------------------------------------------------------------------------------------------------------------------------

</details>

<details>
<summary>

<h4> GET getLogDir.cgi </h4>

**Description:** Fetches the names of logs files available in the Log Directory of the system.

</summary>

**End Point:** /cgi-bin/getLogDir.cgi

**Parameters Required:** None

**Response:**
```json
{
  "logs": {
    "today": [],
    "previous": [
      {
        "fileName": "restart.log",
        "fileSize": "220 B",
        "fileMod": ""
      },
      {
        "fileName": "onlineUpdate.log",
        "fileSize": "2 KB",
        "fileMod": ""
      },
      {
        "fileName": "logs-202504132359.tar.gz",
        "fileSize": "5 MB",
        "fileMod": ""
      },
      {
        "fileName": "logs-202504122359.tar.gz",
        "fileSize": "5 MB",
        "fileMod": ""
      },
      {
        "fileName": "logs-202504112359.tar.gz",
        "fileSize": "6 MB",
        "fileMod": ""
      },
      {
        "fileName": "logs-202504092359.tar.gz",
        "fileSize": "3 MB",
        "fileMod": ""
      },
      {
        "fileName": "logs-202504082359.tar.gz",
        "fileSize": "3 MB",
        "fileMod": ""
      },
      {
        "fileName": "hrRestartAtmpt.log",
        "fileSize": "24 B",
        "fileMod": ""
      },
      {
        "fileName": "foundryminerExec.log",
        "fileSize": "13 MB",
        "fileMod": ""
      },
      {
        "fileName": "foundryminerErr.log",
        "fileSize": "5 KB",
        "fileMod": ""
      },
      {
        "fileName": "checkDirectory.log",
        "fileSize": "52 KB",
        "fileMod": ""
      }
    ]
  },
  "csv": {
    "today": [],
    "previous": [
      {
        "fileName": "Log0414.csv",
        "fileSize": "165 KB",
        "fileMod": ""
      },
      {
        "fileName": "Log0413.csv",
        "fileSize": "346 KB",
        "fileMod": ""
      },
      {
        "fileName": "Log0412.csv",
        "fileSize": "340 KB",
        "fileMod": ""
      },
      {
        "fileName": "Log0411.csv",
        "fileSize": "257 KB",
        "fileMod": ""
      },
      {
        "fileName": "Log0410.csv",
        "fileSize": "210 KB",
        "fileMod": ""
      },
      {
        "fileName": "Log0409.csv",
        "fileSize": "353 KB",
        "fileMod": ""
      },
      {
        "fileName": "Log0408.csv",
        "fileSize": "353 KB",
        "fileMod": ""
      },
      {
        "fileName": "Log0407.csv",
        "fileSize": "353 KB",
        "fileMod": ""
      }
    ]
  }
}

```
**Parameter Specification Table**

----------------------------------------------------------------------------------------------------------------------------------
|Key            | Data-Type|Info|    Valid Values  | Supported <br> by <br>Foundry FW |
|---------------|------------------|-----------|------------|--------------------------|
|logs           |Array             |Array containing the list of all log files|          |   Y        |
|csv            |Array             |Array containing the list of all csv files|           |    Y      |
----------------------------------------------------------------------------------------------------------------------------------
</details>

<details>
<summary>

<h4> GET getMinerInfo.cgi </h4>

**Description:** Fetches the recent significant events occurred on the miner.
 
</summary>

**End Point:**/cgi-bin/getMinerInfo.cgi

**Parameters Required:** None

**Response: **
```
Last Restart: 04/14/25 06:07:27	Exit due to Switch to Sleep-Mode
04/14/25 06:07:39.512 L3 MAIN Miner in Sleep-Mode
04/14/25 06:25:33.214 L3 MAIN Start Mining
.
.
.

```
</details>

<details>
<summary>

<h4> GET  get_ntp_server.cgi </h4>

**Description:** Fetches the ntp server urls to which the miners are configured to currently.

</summary>

**End Point:**/cgi-bin/get_ntp_server.cgi

**Parameters Required: **

**Response: **
```json
{
    "ntpServer0": "0.pool.ntp.org",
    "ntpServer1": "1.pool.ntp.org",
    "ntpServer2": "2.pool.ntp.org"
}
```
</details>

<details>
<summary>

<h4> GET  fetchReleaseNotes.cgi </h4>

**Description:** Fetches the latest release notes.

</summary>

**End Point:**/cgi-bin/fetchReleaseNotes.cgi

**Parameters Required:** None

**Response: **
```json
{
    "versionLogs": [
        {
            "version": "2.4.2",
            "releaseDate": "May 28 2024",
            "firmwareVersion": "2.4.2",
            "dashboardVersion": "1.2.5",
            "MainChanges": [
                {
                    "added": ["",""],
                    "modified": ["",""]
                }
            ],
            "BugFixes": ["",""]
        }
    ],
        /* All the previous release notes are fetched as in the same format above, response snipped for concise documentation*/
}

```

**Parameter Specification Table**

----------------------------------------------------------------------------------------------------------------------------------
|Key        |                |        | Data-Type        |Info          |Valid Values        |Supported <br>by <br>Foundry FW|
|-----------|----------------|--------|------------------|---------------------------------------------------------------|-------------|-----------------------|      
|versionLogs|version         |        |STRING            |Release Version                                                |             |             Y          |      
|           |releaseDate     |        |STRING            |Date of the release                                            |             |             Y          |      
|           |firmwareVersion |        |STRING            |Firmware version included in the release files                 |             |                 Y      |      
|           |dashboardVersion|        |STRING            |Dashboard version included in the release files                |             |                 Y      |      
|           |MainChanges     |added   |Array of Strings  |Array containing all the newly added features                  |             |            Y           |      
|           |                |modified|Array of Strings  |Array containing all the modifications in the existing features|             |                  Y     |      
|           |                |BugFixes|Array of Strings  |Array containing all the bugs fixed                            |             |         Y              |      
-------------------------------------------------------------------------------------------------------------------------------
</details>

<details>
<summary>
<h4> GET getMinerStatus.cgi </h4>

**Description:** Fetches miner related parameters such as firmware version, Miner variant, Controller board type, Miner status and FW compile time.
 
</summary>

**End Point:**/cgi-bin/getMinerStatus.cgi

**Parameters Required:** None

**Response:** 

```json
{
  "STATUS": [
    {
      "STATUS": "S",
      "When": 1744630800,
      "Code": 100,
      "Msg": "FDMiner Status",
      "Description": "FDMiner 2503"
    }
  ],
  "MinerStatus": [
    {
      "BMMiner": "2503",
      "Miner": "Amlogic",
      "Type": "Antminer S19JPROWP",
      "MinerStatus": "Mining",
      "CompileTime": "Mon Mar 31 02:08:42 PM UTC 2025"
    }
  ],
  "id": 1
}
```
</details>

<details>
<summary>

<h4> GET get_system_info.cgi </h4>

**Description:** Fetches System information parameters.

</summary>

**End Point:**/cgi-bin/get_system_info.cgi

**Parameters Required:** None.

**Response:**

```json
{
      "minertype": "Antminer S19 XP",
	"nettype": "DHCP",
	"netdevice": "end0",
	"macaddr": "02:03:00:00:00:05",
	"hostname": "foundry-020300000002",
	"ipaddres": "10.2.30.41",
	"netmask": "255.255.255.0",
	"gateway": "10.2.30.1",
	"dnsservers": "1.1.1.1",
	"system_mode": "GNU/Linux",
	"system_kernel_version": "Linux 6.1.28 #1 SMP PREEMPT Wed May 29 12:17:48 IST 2024",
	"system_filesystem_version": "Tue Jun 25 17:10:32 CST 2024",
	"firmware_type": "test"
      "serinum": "0ca56518acba4a66bb799c17db536063"
}

```
**Parameter Specification Table**

------------------------------------------------------------------------------------------------------------
|Key            |Data-Type         |Info|Valid Values |           |Supported <br>by<br> Foundry FW|
|---------------|------------------|-----------|-----------|-------------------------------|---------------|   
|minertype      |STRING            |Antminer UNKNOWN|      |                      |  Y       |          |
|nettype        |STRING            |DHCP/Static|            |                       |Y|
|netdevice      |STRING            |end0/eth0  |           |                    |Y|
|macaddr        |STRING            |device MAC address ex. '02:01:3A:00:00:50'|         |    | Y              |
|hostname       |STRING            |device username ex. foundry-020150250036| ||   Y|
|ipaddres       |STRING            |device IP address ex. 192.168.0.122|                     |   | Y              |
|netmask        |STRING            |network mask address  ex .255.255.255.0|                  |   |Y                |
|gateway        |STRING            |Deafult gateway ex.192.168.0.1|                  |                     |Y|
|dnsservers     |STRING            |dns server IP: ex. 192.168.0.1/8.8.8.8|   |                |  Y|
|system_mode    |STRING            |GNU/Linux  |             |                |           Y|
|system_kernel_version|STRING            |Linux 6.1.28 #1 SMP PREEMPT Tue Feb 13 14:49:14 IST 2024|          ||Y       |        |Y    |
|system_filesystem_version|STRING            |Thu May 28 02:16:32 CST 2024|           |                |Y       |
|firmware_type  |STRING            |test       |               |                            |Y|
|serinum        |STRING            | 91268714f67c40abbf6857bb1e64394f - Serial Number of CB |   | |Y|
----------------------------------------------------------------------------------------------------------------------------------
</details>

<details>
<summary>

<h4> GET getATStat.cgi </h4>

**Description:** Provides the Chip Level tuning status when the miner is in Autotune Mode (0 signifies Disabled & 1 for Enabled)

</summary>

**End Point:**/cgi-bin/getATStat.cgi

**Parameters Required:** None

**Response: **

```json
{"chipTuningMode":"0"}
```
</details>

<details>
<summary>

<h4> GET  getNetStat.cgi </h4>

**Description:** Fetch device MAC, IP address, fetch total Transferred (tx) and received(rx) bytes of data in device after last reboot, ping speed in milliseconds. 

</summary>

**End Point:**/cgi-bin/getNetStat.cgi

**Parameters Required:** None

**Response:** 

```json
{
"mac":"02:01:3A:00:00:50",
"ip":"192.168.0.122",
"rx":"(69.0 MiB)",
"tx":"(66.6 MiB)",
"speed":"2.543"
}
```
**Parameter Specification Table**

----------------------------------------------------------------------------------------------------------------------------------
|Key            | Data-Type|Info| Valid Values | Supported <br>by <br> Foundry FW |
|---------------|------------------|------------|---------|------------------------|                             
|mac	        |STRING	           |Device MAC address |            |   Y |
|IP             |STRING            |Device ip   |     | Y |
|rx             |STRING            |Data recived over network device |  | Y |
|tx             |STRING            |Data trasfered trough current network device |  | Y |
|speed          |STRING            |speed in ms to transfer 1500 byte packet|           | Y |

----------------------------------------------------------------------------------------------------------------------------------

</details>

<details>
<summary>

<h4> GET liveLogs.cgi </h4>

**Description:** Fetches last 100 lines of real time logs.

</summary>

**End Point:** /cgi-bin/liveLogs.cgi

**Parameters Required:**  None

**Response:** 

```
Data is from line 26306 to line 26405:
12/07/24 06:51:28.300 L4 STAT IT :	45	0	0
12/07/24 06:51:28.300 L4 STAT OT :	71	0	0
12/07/24 06:51:28.300 L4 STAT HT :	71.00
12/07/24 06:51:28.300 L4 STAT F  :490	V:13.80
12/07/24 06:51:28.300 L4 STAT PC : 1.30	EF 19.55
12/07/24 06:51:28.300 L4 STAT FSS:	46	3465	3537	3437	3479
12/07/24 06:51:28.300 L4 STAT 1.3kW	19.5J/TH
12/07/24 06:51:28.300 L4 STAT HB1	AR:	6590	PS:	34812	HR:	66.4TH/s
12/07/24 06:51:28.300 L4 STAT CHR: 66.36	 30MinHR: 66	 1HHR: 66
12/07/24 06:51:28.301 L4 STAT UT:	598965 s
12/07/24 06:51:29.865 L5 HB   HB1 HWE
12/07/24 06:51:31.117 L1 MAIN PID fanSetSpeed	 P: -1.00	 I: 325.00	 D: 0.00	 C: 24 FS: 66	 FSS: 46
12/07/24 06:51:32.041 L5 POOL CPH :	1516500	1516494	1516474.
12/07/24 06:51:34.123 L1 MAIN PID fanSetSpeed	 P: -1.00	 I: 324.00	 D: 0.00	 C: 23 FS: 67	 FSS: 47
12/07/24 06:51:35.281 L0 FAN  Changing Fan Speed 46 -> 47
12/07/24 06:51:37.125 L1 MAIN PID fanSetSpeed	 P: -1.00	 I: 323.00	 D: 0.00	 C: 23 FS: 67	 FSS: 47
12/07/24 06:51:37.148 L5 NETW Network - OK
12/07/24 06:51:38.123 L0 MAIN ATS 1 
12/07/24 06:51:38.123 L0 MAIN ##   ## voltage Selected is at Stable ##   ##: 13.80
12/07/24 06:51:38.123 L0 MAIN voltage before limit & set value: 13.80
12/07/24 06:51:38.124 L0 MAIN EnabledHB THR: 66.67	 HRAfterLastVoltUpdate: 66.37	 New Calc V : 13.80
12/07/24 06:51:40.121 L1 MAIN PID fanSetSpeed	 P: -1.00	 I: 322.00	 D: 0.00	 C: 23 FS: 67	 FSS: 47
12/07/24 06:51:40.269 L5 HB   HB1: 0 BD 7396797.5 / 262144
12/07/24 06:51:41.051 L5 POOL Share 34822 Accepted
12/07/24 06:51:43.130 L1 MAIN PID fanSetSpeed	 P: -1.00	 I: 321.00	 D: 0.00	 C: 23 FS: 67	 FSS: 47
12/07/24 06:51:46.121 L1 MAIN PID fanSetSpeed	 P: -1.00	 I: 320.00	 D: 0.00	 C: 23 FS: 67	 FSS: 47
12/07/24 06:51:49.120 L1 MAIN PID fanSetSpeed	 P: -1.00	 I: 319.00	 D: 0.00	 C: 23 FS: 67	 FSS: 47
12/07/24 06:51:52.043 L5 POOL CPH :	1516520	1516518	1516509.
12/07/24 06:51:52.118 L1 MAIN PID fanSetSpeed	 P: -1.00	 I: 318.00	 D: 0.00	 C: 23 FS: 67	 FSS: 47
12/07/24 06:51:55.123 L1 MAIN PID fanSetSpeed	 P: -1.00	 I: 317.00	 D: 0.00	 C: 23 FS: 67	 FSS: 47
12/07/24 06:51:58.120 L1 MAIN PID fanSetSpeed	 P: -1.00	 I: 316.00	 D: 0.00	 C: 23 FS: 67	 FSS: 47
12/07/24 06:52:00.345 L4 STAT CPI:	0
12/07/24 06:52:00.346 L4 STAT PH :	1	1	0
12/07/24 06:52:00.346 L4 STAT TPA:	34693	 \ 	117
12/07/24 06:52:00.346 L4 STAT PA :	34666	 \ 	117
12/07/24 06:52:00.346 L4 STAT IT :	44	0	0
12/07/24 06:52:00.346 L4 STAT OT :	70	0	0
12/07/24 06:52:00.346 L4 STAT HT :	70.00
12/07/24 06:52:00.346 L4 STAT F  :490	V:13.80
12/07/24 06:52:00.346 L4 STAT PC : 1.29	EF 19.64
12/07/24 06:52:00.346 L4 STAT FSS:	47	3500	3484	3516	3533
12/07/24 06:52:00.346 L4 STAT 1.3kW	19.6J/TH
12/07/24 06:52:00.346 L4 STAT HB1	AR:	6591	PS:	34813	HR:	65.8TH/s
12/07/24 06:52:00.346 L4 STAT CHR: 65.77	 30MinHR: 66	 1HHR: 66

.
.
.
.
.

```
</details>

<details>
<summary>

<h4> GET getAtStatus.cgi </h4>

**Description:** Fetches the Autotune optimisation status and completion percentage.

</summary>

**End Point:**/cgi-bin/getAtStatus.cgi

**Parameters Required:** None

**Response: **

```json
{
	"status":	"AT completed Optimizing",
	"percentage":	100
}

```
</details>

<details>
<summary>

<h4> GET log.cgi </h4>

**Description:** Fetches the Miner Log.

</summary>

**End Point:** /cgi-bin/log.cgi

**Parameters Required:** None.

**Response: **

```
2/07/24 06:55:35.120 L1 MAIN PID fanSetSpeed	 P: 0.00	 I: 324.00	 D: 0.00	 C: 25 FS: 65	 FSS: 45
12/07/24 06:55:38.121 L1 MAIN PID fanSetSpeed	 P: 0.00	 I: 324.00	 D: 0.00	 C: 25 FS: 65	 FSS: 45
12/07/24 06:55:41.122 L1 MAIN PID fanSetSpeed	 P: 0.00	 I: 324.00	 D: 0.00	 C: 25 FS: 65	 FSS: 45
12/07/24 06:55:44.115 L1 MAIN PID fanSetSpeed	 P: 0.00	 I: 324.00	 D: 0.00	 C: 25 FS: 65	 FSS: 45
12/07/24 06:55:46.118 L0 MAIN ATS 1 
12/07/24 06:55:46.118 L0 MAIN ##   ## voltage Selected is at Stable ##   ##: 13.80
12/07/24 06:55:46.119 L0 MAIN voltage before limit & set value: 13.80
12/07/24 06:55:46.119 L0 MAIN EnabledHB THR: 66.67	 HRAfterLastVoltUpdate: 66.61	 New Calc V : 13.80
12/07/24 06:55:47.117 L1 MAIN PID fanSetSpeed	 P: 0.00	 I: 324.00	 D: 0.00	 C: 25 FS: 65	 FSS: 45
12/07/24 06:55:50.118 L1 MAIN PID fanSetSpeed	 P: 0.00	 I: 324.00	 D: 0.00	 C: 25 FS: 65	 FSS: 45
12/07/24 06:55:53.123 L1 MAIN PID fanSetSpeed	 P: 0.00	 I: 324.00	 D: 0.00	 C: 25 FS: 65	 FSS: 45
12/07/24 06:55:56.117 L0 MAIN Waiting for all pool Status
12/07/24 06:55:57.118 L1 MAIN PID fanSetSpeed	 P: 0.00	 I: 324.00	 D: 0.00	 C: 25 FS: 65	 FSS: 45
12/07/24 06:56:00.118 L1 MAIN PID fanSetSpeed	 P: 0.00	 I: 324.00	 D: 0.00	 C: 25 FS: 65	 FSS: 45
12/07/24 06:56:03.121 L1 MAIN PID fanSetSpeed	 P: 0.00	 I: 324.00	 D: 0.00	 C: 25 FS: 65	 FSS: 45
12/07/24 06:56:06.117 L1 MAIN PID fanSetSpeed	 P: 1.00	 I: 325.00	 D: 1.00	 C: 28 FS: 62	 FSS: 41
12/07/24 06:56:06.555 L0 FAN  Changing Fan Speed 45 -> 41
12/07/24 06:56:09.117 L1 MAIN PID fanSetSpeed	 P: 1.00	 I: 326.00	 D: 0.00	 C: 28 FS: 62	 FSS: 41
12/07/24 06:56:12.122 L1 MAIN PID fanSetSpeed	 P: 1.00	 I: 327.00	 D: 0.00	 C: 28 FS: 62	 FSS: 41
12/07/24 06:56:15.120 L1 MAIN PID fanSetSpeed	 P: 1.00	 I: 328.00	 D: 0.00	 C: 28 FS: 62	 FSS: 41
12/07/24 06:56:18.120 L1 MAIN PID fanSetSpeed	 P: 1.00	 I: 329.00	 D: 0.00	 C: 28 FS: 62	 FSS: 41
12/07/24 06:56:21.120 L1 MAIN PID fanSetSpeed	 P: 1.00	 I: 330.00	 D: 0.00	 C: 28 FS: 62	 FSS: 41
12/07/24 06:56:24.116 L1 MAIN PID fanSetSpeed	 P: 1.00	 I: 331.00	 D: 0.00	 C: 28 FS: 62	 FSS: 41
12/07/24 06:56:27.116 L1 MAIN PID fanSetSpeed	 P: 1.00	 I: 332.00	 D: 0.00	 C: 28 FS: 62	 FSS: 41
12/07/24 06:56:30.122 L1 MAIN PID fanSetSpeed	 P: 1.00	 I: 333.00	 D: 0.00	 C: 28 FS: 62	 FSS: 41
12/07/24 06:56:33.123 L1 MAIN PID fanSetSpeed	 P: 1.00	 I: 334.00	 D: 0.00	 C: 28 FS: 62	 FSS: 41
12/07/24 06:56:36.123 L1 MAIN PID fanSetSpeed	 P: 1.00	 I: 335.00	 D: 0.00	 C: 28 FS: 62	 FSS: 41
12/07/24 06:56:39.116 L1 MAIN PID fanSetSpeed	 P: 1.00	 I: 336.00	 D: 0.00	 C: 28 FS: 62	 FSS: 41
12/07/24 06:56:42.122 L1 MAIN PID fanSetSpeed	 P: 1.00	 I: 337.00	 D: 0.00	 C: 28 FS: 62	 FSS: 41
12/07/24 06:56:45.114 L1 MAIN PID fanSetSpeed	 P: 1.00	 I: 338.00	 D: 0.00	 C: 29 FS: 61	 FSS: 40
12/07/24 06:56:46.551 L0 FAN  Changing Fan Speed 41 -> 40
12/07/24 06:56:48.120 L1 MAIN PID fanSetSpeed	 P: 1.00	 I: 339.00	 D: 0.00	 C: 29 FS: 61	 FSS: 40

```


> Note: <br>
> Logs.cgi is currently implemented as log.cgi, and was supported in the previous versions (prior to 2.4.4). Logs.cgi will be decommissioned in future versions. <br>

</details>

<details>
<summary>

<h4> GET  getAutoConf.cgi </h4>

**Description:** Fetches pre-defined/user entered flag (0/1) to control online updates and auto-rename functionality.

</summary>

**End Point:**/cgi-bin/getAutoConf.cgi

**Parameters Required:** None

**Response:** 

```json
{
"autoUpdate": 0,
"autoCheckUpdate": 0,
"autoHostRename": 0
}
```
**Parameter Specification Table**

----------------------------------------------------------------------------------------------------------------------------------
|Key            | Data-Type        |Info       |Valid Values         |Supported <br>by<br>Foundry FW |
|---------------|------------------|-----------|----------------------|-------------------------------|
|autoUpdate     |INT               |  0: auto firmware update wont be carried out  <br>   1: auto firmware update will be carried out     |         |   Y      |                            
|autoCheckUpdate|INT               |  0: auto firmware update check wont be carried out <br>   1: auto firmware update check will be carried out     |      |      Y |
|autoHostRename|	INT	|             0: auto user rename wont be carried out <br>   1: auto user rename will be carried out |      | Y     |
----------------------------------------------------------------------------------------------------------------------------------

</details>

<details>
<summary>

<h4> GET getPermissionStatus.cgi </h4>

**Description:** Fetches the access status of the system, below are the return values and their respective access levels:	
100 - Write
150 - Read
200 - Denied

</summary>

**End Point:**/cgi-bin/getPermissionStatus.cgi

**Parameters Required:** None

**Response:**

```json
{
  "AccessStatus": 100
}

```
</details>

<details>
<summary>

<h4> GET getBlockFoundInfo.cgi </h4>

**Description:** Fetch the info related to the previous found block.
Returns “File Not Found” if not available.

</summary>

**End Point:**/cgi-bin/getBlockFoundInfo.cgi

**Parameters Required:** None

**Response: **

```
03/28/25 15:22:48 Block Found Diff 1288607092084618.8/113757508810854.0
```
</details>

<details>
<summary>
<h4> GET getBoardTemp.cgi </h4>

**Description:** Fetches Board Temperature in degree centigrades(°C).

</summary>

**End Point:** /cgi-bin/getBoardTemp.cgi

**Parameters Required:** None

**Response:**

```json
{ "boardTemperature": 48 }
```
**Parameter Specification Table**

----------------------------------------------------------------------------------------------------------------------------------
|Key            | Data-Type        |   Info  |Valid Values  |Supported <br> by <br> Foundry FW |
|---------------|------------------|-------------|-----------|-----------------------------------|
|boardTemperature|INT              |CB temp in °C|           |     Y                             |

----------------------------------------------------------------------------------------------------------------------------------
</details>

<details>
<summary>

<h4> GET getRamData.cgi </h4>

**Description:** Fetches RAM usage Data from the system.

</summary>

**End Point:** /cgi-bin/getRamData.cgi

**Parameters Required:** None.

**Response:** 

```json
{
    "total": "402264",
    "used": "51512",
    "shared": "12240",
    "buffer": "8652",
    "available": "350752",
    "%used": "12.8055",
    "%available": "87.1945"
}
```
**Parameter Specification Table**

--------------------------------------------------------------------------------------------------------------
| Key        | Data Type | Description                      | Valid Values | Supported by Foundry FW |
|------------|-----------|----------------------------------|---------------|--------------------------|
| total      | STRING    | Total RAM available              |               | Y                        |
| used       | STRING    | The amount currently in use      |               | Y                        |
| shared     | STRING    | Memory shared between processes  |               | Y                        |
| buffer     | STRING    | Memory used for buffers          |               | Y                        |
| available  | STRING    | Remaining free memory            |               | Y                        |
| %used      | STRING    | Percentage of used memory        |               | Y                        |
| %available | STRING    | Percentage of available memory   |               | Y                        |
---------------------------------------------------------------------------------------------------------------
</details>

<details>
<summary>

<h4> GET pools.cgi </h4>

**Description:** Fetches all the configured pool data in the order of priority.

</summary>

**End Point:** /cgi-bin/pools.cgi

**Parameters Required:** None.

Response:
```json
{
	"STATUS": [
		{
			"STATUS": "S",
			"When": 1719404628,
			"Code": 7,
			"Msg": "3 Pool(s)",
			"Description": "BCFMiner 2.4.3 Test"
		}
	],
	"POOLS": [
		{
			"POOL": 0,
			"URL": "stratum+tcp://btc.foundryusapool.com:3333",
			"Status": "Active",
			"Priority": 0,
			"Quota": 0,
			"Getworks": 368,
			"Accepted": 705,
			"Rejected": 2,
			"Discarded": 0,
			"Stale": 1,
			"Get Failures": 0,
			"Remote Failures": 0,
			"User": "ccc.S19XP_B1",
			"Last Share Time": "1719404597",
			"Diff": "524K",
			"Diff1 Shares": 0,
			"Proxy Type": "",
			"Proxy": "",
			"Difficulty Accepted": 4191891,
			"Difficulty Rejected": 0,
			"Difficulty Stale": 627693,
			"Last Share Difficulty": 4191891,
			"Has Stratum": true,
			"Stratum Active": true,
			"Stratum URL": "btc.foundryusapool.com",
			"Has GBT": false,
			"Best Share": 787387275
		},
		/*Pool2 and Pool 3 Detailes will also be fetched in the above format*/
		/** Response Modified for documentation purpose, Repetative Data patterns skipped for presice documentation**/
		],
	"id":	1
}
```
**Parameter Specification Table**

| Key              | Field             | Data-Type       | Info                                                                                                            | Valid Values | Supported by Foundry FW |
|------------------|-------------------|-----------------|-----------------------------------------------------------------------------------------------------------------|--------------|------------------------|
| STATUS           | STATUS            | STRING          | S - Success F - Failure                                                                                          |              | Y                      |
|                  | When              | time_t or long int | Number of seconds elapsed since 00:00:00 hours, GMT (Greenwich Mean Time), January 1, 1970                       |              | Y                      |
|                  | Code              | INT             | Code that represents pools response (7)                                                                         |              | Y                      |
|                  | Msg               | STRING          | Describes the number of pools data                                                                              |              | Y                      |
|                  | Description       | STRING          | Describes the type of Firmware and its version                                                                  |              | Y                      |
| POOLS            | POOL              | INT             | Pool index 0, 1 & 2                                                                                             |              | Y                      |
|                  | URL               | STRING          | Contains pool info in the format stratum+tcp://url:port                                                         |              | Y                      |
|                  | Status            | STRING          | Status of this pool. Active - If pool is being used for mining Alive - If pool is available for mining Dead - If pool is currently unavailable for mining |              | Y                      |
|                  | Priority          | INT             | Priority of the pool for mining. Priority 0 means highest priority & 2 means low priority                        |              | Y                      |
|                  | Quota             |                 |                                                                                                                 |              | N                      |
|                  | Getworks          | unsigned Int    | Total no of mining.notify or pool jobs received in this pool                                                    |              | Y                      |
|                  | Accepted          | unsigned Int    | No of shares accepted by this pool                                                                              |              | Y                      |
|                  | Rejected          | unsigned Int    | No of shares rejected by this pool                                                                              |              | Y                      |
|                  | Discarded         |                 |          |              | N                      |
|                  | Stale             | unsigned Int    | No of stale shares submitted to this pool                                                                       |              | Y                      |
|                  | Get Failures      |                 |        |              | N                      |
|                  | Remote Failures   |                 |                                      |              | N                      |
|                  | User              | STRING          | Pool workername                                                                                                  |              | Y                      |
|                  | Last Share Time   | STRING          | Last share time in Epoch                                                                                         |              | Y                      |
|                  | Diff              | STRING          | Pool difficulty in terms of 1000                                                                                 |              | Y                      |
|                  | Diff1 Shares      |                 |      |              | N                      |
|                  | Proxy Type        |                 |         |              | N                      |
|                  | Proxy             |                 |    |              | N                      |
|                  | Difficulty Accepted | unsigned Int  | Difficulty of the last pool accepted share                                                                      |              | Y                      |
|                  | Difficulty Rejected | unsigned Int  | Difficulty of the last pool rejected share                                                                      |              | Y                      |
|                  | Difficulty Stale  | unsigned Int    | Difficulty of the last stale share                                                                               |              | Y                      |
|                  | Last Share Difficulty | unsigned Int | Difficulty of the last share submitted to pool                                                                  |              | Y                      |
|                  | Has Stratum       | Bool            | true                                                                                                            |              | Y                      |
|                  | Stratum Active    | Bool            | true               |              | Y                      |
|                  | Stratum URL       | STRING          | Pool address                                                                                                    |              | Y                      |
|                  | Has GBT           | Bool            | false                                                                                                           |              | Y                      |
|                  | Best Share        | unsigned Int    | Highest difficulty of the pool accepted share                                                                  |              | Y                      |
|                  | id                | INT             | id of the message or priority of the message. Usually 1                                                        |              | Y                      |
----------------------------------------------------------------------------------------------------------------------------------------------------------------------
</details>

<details>
<summary>

<h4> GET  stats.cgi </h4>

**Description:** Fetch Miner data for each ASIC chain on the HashBoard.

</summary>

**End Point:** /cgi-bin/stats.cgi

**Parameters Required:** None.

**Response:**

```json
{
	"STATUS":	[{
			"STATUS":	"S",
			"When":	1719161976,
			"Code":	70,
			"Msg":	"BCFMiner Stats",
			"Description":	"BCFMiner 2.4.2 Test2"
		}],
	"STATS":	[{
			"BMMiner":	"2.4.2 Test2",
			"Miner":	"FCB V2.2",
			"CompileTime":	"Wed Jun 12 02:16:32 CST 2024",
			"Type":	"Antminer S19 XP"
		}, {
			"STATS":	0,
			"ID":	"BTM_SOC0",
			"Elapsed":	23722,
			"Calls":	0,
			"Wait":	0,
			"Max":	0,
			"Min":	99999999,
			"GHS 5s":	94000,
			"GHS av":	93000,
			"rate_30m":	93000,
			"Mode":	2,
			"miner_count":	3,
			"frequency":	320,
			"fan_num":	4,
			"fan1":	5853,
			"fan2":	5798,
			"fan3":	5797,
			"fan4":	5758,
			"temp_num":	3,
			"temp1":	61.5,
			"temp2_1":	53.5,
			"temp2":	62,
			"temp2_2":	54,
			"temp3":	65,
			"temp2_3":	55.5,
			"temp_pcb1":	"48-48-56-56",
			"temp_chip1":	"53-53-61-61",
			"temp_pic1":	"38-38-46-46",
			"temp_pcb2":	"49-49-57-57",
			"temp_chip2":	"54-54-62-62",
			"temp_pic2":	"39-39-47-47",
			"temp_pcb3":	"50-50-60-60",
			"temp_chip3":	"55-55-65-65",
			"temp_pic3":	"40-40-50-50",
			"temp_pcb4":	"0-0-0-0",
			"temp_chip4":	"0-0-0-0",
			"temp_pic4":	"0-0-0-0",
			"total_rateideal":	88000,
			"rate_unit":	"GH",
			"total_freqavg":	320,
			"total_acn":	1679,
			"total rate":	94.228668212890625,
			"temp_max":	65,
			"no_matching_work":	0,
			"chain_acn1":	559,
			"chain_acn2":	559,
			"chain_acn3":	559,
			"chain_acs1":	"oooooooooo oooooooooo oooooooooo oooooooooo oooooooooo oooooooooo oooooooooo oooooooooo oooooooooo oooooooooo oooooooooo",
			"chain_acs2":	"oooooooooo oooooooooo oooooooooo oooooooooo oooooooooo oooooooooo oooooooooo oooooooooo oooooooooo oooooooooo oooooooooo",
			"chain_acs3":	"oooooooooo oooooooooo oooooooooo oooooooooo oooooooooo oooooooooo oooooooooo oooooooooo oooooooooo oooooooooo oooooooooo",
			"chain_acs4":	"",
			"chain_hw1":	2,
			"chain_hw2":	1,
			"chain_hw3":	3,
			"chain_rate1":	"29",
			"chain_rate2":	"32",
			"chain_rate3":	"32",
			"chain_rate4":	"",
			"freq1":	320,
			"freq2":	320,
			"freq3":	320,
			"freq4":	0,
			"miner_version":	"FCB V2.2",
			"miner_id":	"811cc44a6f41a854"
		}],
	"id":	1
}

```

</details>

<details>
<summary>

<h4> GET getChipLevelData.cgi </h4>

**Description:** Fetches stats of each chain of ASICs in the HB, the cgi fetches 
major chiplevel parameters like health, frequency,Chiplevel HashRate and Hardware errors in each chip.

</summary>

**End Point:**/cgi-bin/getChipLevelData.cgi

**Parameters Required:** None

**Response:** 
```json
{
  "STATUS": [
    {
      "STATUS": "S",
      "When": 1744626550,
      "Code": 88,
      "Msg": "FDMiner ChipLevel Info",
      "Description": "FDMiner 2503"
    }
  ],
  "ChipLevel": {
    "asicFreqChain1": [
      [515, 515, 515, 515, 515, 515, 515, 515, 515, 515],
      [515, 515, 515, 515, 515, 515, 515, 515, 515, 515],
      [515, 515, 515, 515, 515, 515, 515, 515, 515, 515],
      [515, 515, 515, 515, 515, 515, 515, 515, 515, 515],
      [515, 515, 515, 515, 515, 515, 515, 515, 515, 515],
      [515, 515, 515, 515, 515, 515, 515, 515, 515, 515],
      [515, 515, 515, 515, 515, 515, 515, 515, 515, 515],
      [515, 515, 515, 515, 515, 515, 515, 515, 515, 515],
      [515, 515, 515, 515, 515, 515, 515, 515, 515, 515],
      [515, 515, 515, 515, 515, 515, 515, 515, 515, 515],
      [515, 515, 515, 515, 515, 515, 515, 515, 515, 515]
    ],
    "asicHRChain1": [
      [478, 453, 459, 458, 483, 469, 458, 488, 456, 489],
      [464, 464, 480, 481, 453, 479, 470, 464, 463, 469],
      [467, 472, 478, 460, 471, 482, 488, 463, 466, 483],
      [448, 464, 465, 458, 480, 487, 501, 471, 469, 457],
      [490, 490, 486, 459, 487, 462, 457, 443, 476, 466],
      [483, 462, 474, 490, 475, 484, 466, 482, 488, 488],
      [475, 472, 435, 475, 490, 483, 455, 462, 462, 467],
      [457, 491, 430, 456, 462, 483, 463, 461, 453, 479],
      [451, 433, 454, 487, 454, 473, 481, 488, 446, 459],
      [475, 446, 482, 498, 485, 470, 472, 490, 472, 488],
      [465, 457, 465, 468, 446, 479, 457, 441, 465, 483]
    ],
    "asicHWEChain1": [
      [0, 0, 0, 0, 0, 0, 0, 0, 0, 0],
      [0, 0, 0, 0, 0, 0, 0, 0, 0, 0],
      [0, 0, 0, 0, 0, 0, 0, 0, 0, 0],
      [0, 0, 0, 0, 0, 0, 0, 0, 0, 0],
      [0, 0, 0, 0, 0, 0, 0, 0, 0, 0],
      [0, 0, 0, 0, 0, 0, 0, 0, 0, 0],
      [0, 0, 0, 0, 0, 0, 0, 0, 0, 0],
      [0, 0, 0, 0, 0, 0, 0, 0, 0, 0],
      [0, 0, 0, 0, 0, 0, 0, 0, 0, 0],
      [0, 0, 0, 0, 0, 0, 0, 0, 0, 0],
      [0, 0, 0, 0, 0, 0, 0, 0, 0, 0]
    ],
    "asicHealthChain1": [
      [103, 99, 101, 100, 103, 100, 102, 103, 101, 103],
      [101, 100, 101, 100, 98, 101, 102, 99, 101, 101],
      [102, 102, 101, 101, 99, 103, 103, 100, 99, 102],
      [102, 101, 103, 101, 101, 103, 103, 101, 101, 102],
      [101, 103, 102, 100, 103, 101, 100, 100, 102, 99],
      [101, 100, 100, 103, 102, 102, 102, 101, 103, 102],
      [101, 102, 98, 101, 103, 103, 99, 100, 100, 101],
      [100, 103, 97, 100, 101, 103, 103, 101, 101, 101],
      [100, 99, 101, 103, 101, 99, 103, 103, 99, 101],
      [103, 100, 103, 103, 102, 103, 102, 102, 100, 101],
      [100, 101, 103, 101, 100, 102, 101, 102, 100, 102]
    ],
    "asicFreqChain2": [
      [515, 515, 515, 515, 515, 515, 515, 515, 515, 515],
      [515, 515, 515, 515, 515, 515, 515, 515, 515, 515],
      [515, 515, 515, 515, 515, 515, 515, 515, 515, 515],
      [515, 515, 515, 515, 515, 515, 515, 515, 515, 515],
      [515, 515, 515, 515, 515, 515, 515, 515, 515, 515],
      [515, 515, 515, 515, 515, 515, 515, 515, 515, 515],
      [515, 515, 515, 515, 515, 515, 515, 515, 515, 515],
      [515, 515, 515, 515, 515, 515, 515, 515, 515, 515],
      [515, 515, 515, 515, 515, 515, 515, 515, 515, 515],
      [515, 515, 515, 515, 515, 515, 515, 515, 515, 515],
      [515, 515, 515, 515, 515, 515, 515, 515, 515, 515]
    ],
    "asicHRChain2": [
      [449, 451, 486, 461, 456, 488, 454, 520, 475, 488],
      [497, 477, 467, 493, 466, 469, 488, 444, 481, 461],
      [461, 489, 443, 459, 471, 440, 485, 484, 488, 461],
      [489, 467, 458, 476, 448, 448, 461, 467, 476, 461],
      [476, 464, 464, 491, 443, 466, 487, 476, 443, 476],
      [467, 487, 488, 479, 484, 467, 488, 497, 488, 471],
      [470, 458, 441, 471, 508, 469, 458, 473, 451, 488],
      [488, 483, 489, 458, 479, 472, 441, 463, 470, 481],
      [483, 444, 490, 444, 460, 460, 488, 492, 467, 468],
      [469, 464, 489, 454, 457, 452, 467, 471, 477, 460],
      [480, 451, 483, 469, 433, 459, 476, 436, 450, 489]
    ],
    "asicHWEChain2": [
      [0, 0, 0, 0, 0, 0, 0, 0, 0, 0],
      [0, 0, 0, 0, 0, 0, 0, 0, 0, 0],
      [0, 0, 0, 0, 0, 0, 0, 0, 0, 0],
      [0, 0, 0, 0, 0, 0, 0, 0, 0, 0],
      [0, 0, 0, 0, 0, 0, 0, 0, 0, 0],
      [0, 0, 0, 0, 0, 0, 0, 0, 0, 0],
      [0, 0, 0, 0, 0, 0, 0, 0, 0, 0],
      [0, 0, 0, 0, 0, 0, 0, 0, 0, 0],
      [0, 0, 0, 0, 0, 0, 0, 0, 0, 0],
      [0, 0, 0, 0, 0, 0, 0, 0, 0, 0],
      [0, 0, 0, 0, 0, 0, 0, 0, 0, 0]
    ],
    "asicHealthChain2": [
      [99, 98, 103, 102, 101, 102, 101, 104, 100, 103],
      [103, 103, 100, 101, 102, 101, 104, 99, 101, 101],
      [100, 103, 100, 101, 103, 99, 100, 102, 102, 101],
      [103, 102, 102, 103, 97, 101, 99, 102, 102, 100],
      [101, 102, 100, 102, 99, 101, 103, 103, 99, 102],
      [101, 101, 104, 101, 103, 98, 104, 103, 103, 102],
      [102, 102, 101, 102, 103, 100, 102, 102, 99, 103],
      [103, 103, 103, 100, 102, 100, 101, 101, 101, 101],
      [101, 99, 103, 98, 100, 99, 102, 102, 101, 101],
      [101, 101, 101, 101, 103, 101, 101, 101, 100, 99],
      [101, 99, 100, 101, 98, 101, 103, 98, 99, 102]
    ],
    "asicFreqChain3": [
      [515, 515, 515, 515, 515, 515, 515, 515, 515, 515],
      [515, 515, 515, 515, 515, 515, 515, 515, 515, 515],
      [515, 515, 515, 515, 515, 515, 515, 515, 515, 515],
      [515, 515, 515, 515, 515, 515, 515, 515, 515, 515],
      [515, 515, 515, 515, 515, 515, 515, 515, 515, 515],
      [515, 515, 515, 515, 515, 515, 515, 515, 515, 515],
      [515, 515, 515, 515, 515, 515, 515, 515, 515, 515],
      [515, 515, 515, 515, 515, 515, 515, 515, 515, 515],
      [515, 515, 515, 515, 515, 515, 515, 515, 515, 515],
      [515, 515, 515, 515, 515, 515, 515, 515, 515, 515],
      [515, 515, 515, 515, 515, 515, 515, 515, 515, 515]
    ],
    "asicHRChain3": [
      [481, 487, 460, 451, 469, 484, 485, 451, 471, 463],
      [475, 479, 462, 442, 469, 488, 450, 493, 473, 470],
      [472, 455, 475, 474, 482, 470, 484, 453, 451, 479],
      [488, 468, 461, 485, 443, 446, 474, 457, 471, 473],
      [454, 476, 491, 474, 461, 481, 479, 457, 454, 489],
      [454, 464, 465, 462, 466, 484, 484, 461, 470, 458],
      [466, 469, 462, 456, 465, 464, 478, 455, 473, 469],
      [477, 478, 489, 463, 481, 489, 488, 493, 482, 460],
      [469, 478, 469, 444, 444, 464, 496, 447, 432, 439],
      [464, 479, 464, 483, 490, 451, 465, 488, 446, 466],
      [497, 466, 456, 470, 442, 466, 449, 463, 440, 434]
    ],
    "asicHWEChain3": [
      [0, 0, 0, 0, 0, 0, 0, 0, 0, 0],
      [0, 0, 0, 0, 0, 0, 0, 0, 0, 0],
      [0, 0, 0, 0, 0, 0, 0, 0, 0, 0],
      [0, 0, 0, 0, 0, 0, 0, 0, 0, 0],
      [0, 0, 0, 0, 0, 0, 0, 0, 0, 0],
      [0, 0, 0, 0, 0, 0, 0, 0, 0, 0],
      [0, 0, 0, 0, 0, 0, 0, 0, 0, 0],
      [0, 0, 0, 0, 0, 0, 0, 0, 0, 0],
      [0, 0, 0, 0, 0, 0, 0, 0, 0, 0],
      [0, 0, 0, 0, 0, 0, 0, 0, 0, 0],
      [0, 0, 0, 0, 0, 0, 0, 0, 0, 0]
    ],
    "asicHealthChain3": [
      [101, 104, 99, 101, 100, 100, 102, 100, 102, 101],
      [102, 100, 100, 99, 100, 103, 100, 103, 102, 100],
      [103, 100, 102, 100, 102, 103, 101, 99, 101, 102],
      [102, 100, 99, 102, 99, 99, 100, 99, 100, 102],
      [99, 102, 101, 103, 100, 102, 102, 100, 100, 103],
      [101, 99, 100, 101, 103, 102, 102, 101, 99, 98],
      [100, 101, 101, 100, 100, 100, 100, 99, 102, 102],
      [102, 102, 103, 100, 101, 103, 102, 103, 102, 101],
      [103, 102, 100, 99, 99, 101, 103, 101, 98, 100],
      [100, 103, 101, 103, 103, 101, 100, 103, 98, 103],
      [104, 102, 101, 100, 97, 101, 100, 100, 97, 96]
    ]
  },
  "id": 1
}

```
</details>

<details>
<summary>

<h4> GET getReleaseNote.cgi </h4>

**Description:** Fetches the Release Notes from the system server only if new releases are available.

</summary>

**End Point:** /cgi-bin/getReleaseNote.cgi

**Parameters Required:** None

**Response:**
*Response sent only if any new releases are available to be updated.

Expected Response if new releases available:
```
" 2.4.2       * this update is a patch for bug fix #252525   ....................."
```

Expected Response if no new releases available:
```
{"stats":"error","code":"U001","msg":"release note missing!"}"
```
</details>

<details>
<summary>

<h4> GET prodata.cgi </h4>

**Description:** Fetches frequency, Health, Hardware errors and Hash Rates of individual         ASIC in the miner along with other details.

</summary>

**End Point:** /cgi-bin/prodata.cgi

**Parameters Required:** None.

**Response: **
```json
{
	"STATUS":	[{
			"STATUS":	"S",
			"When":	1733556115,
			"Code":	99,
			"Msg":	"BCFMiner ProData",
			"Description":	"BCFMiner 2.4.7"
		}],
	"PROData":	{
		"Miner Status":	"Mining",
		"Miner Name":	"FoundryCBMiner",
		"Voltage":	"13.80",
		"Power":	"1.28",
		"Efficiency":	"19.34",
		"FanMode":	0,
		"FanSpeed":	45,
		"manualFanSpeed":	100,
		"HB1State":	1,
		"HB2State":	0,
		"HB3State":	0,
		"throttle Mode":	"false",
		"throttleHR":	-1,
		"throttleFreq":	-1,
		"Miner Mode":	0,
		"Mining Mode":	0,
		"TargetHR":	200,
		"ShutDownTemp":	90,
		"targetChipTemp":	70,
		"maxHrRestartAttempt":	"5",
		"hrThreshold":	"20",
		"maxErrRestart":	"10",
		"minFans":	"4",
		"pool1Port":	3333,
		"pool1PW":	"x",
		"pool2Port":	443,
		"pool2PW":	"x",
		"pool3Port":	25,
		"pool3PW":	"x",
		"Xcord":	"x",
		"Ycord":	"y",
		"Zcord":	"z"
	},
	"id":	1
}
```
**Parameter Specification Table**

--------------------------------------------------------------------------------------------------------------------------------------------------------------
| Key                | Data Type         | Description                                                      | Valid Values                                                                                 | Supported by Foundry FW |
|--------------------|-------------------|------------------------------------------------------------------|----------------------------------------------------------------------------------------------|------------------------|
| STATUS             | STRING            | S - Success, F - Failure                                         | S, F                                                                                         | Y                      |
| When               | time_t or long int| Seconds since 00:00:00 GMT, January 1, 1970                     |                                                                                              | Y                      |
| Code               | INT               | Code representing prodataresponse                                |                                                                                              | Y                      |
| Msg                | STRING            | Describes the type of message                                    |                                                                                              | Y                      |
| Description        | STRING            | Describes the firmware type and version                          |                                                                                              | Y                      |
| Miner Status       | STRING            | Status of the miner (e.g., Starting, Mining, Sleeping)           | Starting, Booting, Mining, Sleeping, Disable HB, Enable PSU, HB Init, Throttle Mode, Restarting | Y                      |
| Miner Name         | STRING            | Machine name to distinguish between miners                       | Default value: FoundryCBMiner                                                                 | Y                      |
| Voltage            | STRING            | Voltage delivered to Hashboards                                  |                                                                                              | Y                      |
| Power              | STRING            | Estimated power consumption of the miner in KW                  |                                                                                              | Y                      |
| Efficiency         | STRING            | Estimated efficiency of the miner in J/TH                       |                                                                                              | Y                      |
| FanMode            | INT               | Current fan mode (0: Air-cooled, 1: Immersion, 2: Manual)       | 0, 1, 2                                                                                     | Y                      |
| FanSpeed           | INT               | Current speed of fans in %                                       |                                                                                              | Y                      |
| manualFanSpeed     | INT               | User-set manual fan speed for Manual Fan Control                |                                                                                              | Y                      |
| HB1State           | INT               | Hashboard 1 state                                               | 1 (Enabled), 2 (Disabled)                                                                    | Y                      |
| HB2State           | INT               | Hashboard 2 state                                               | 1 (Enabled), 2 (Disabled)                                                                    | Y                      |
| HB3State           | INT               | Hashboard 3 state                                               | 1 (Enabled), 2 (Disabled)                                                                    | Y                      |
| throttle Mode      | STRING            | Current state of throttle mode (true - on, false - off)           | true, false                                                                                  | Y                      |
| throttleFreq       | INT               | Throttled frequency in MHz                                       |                                                                                              | Y                      |
| throttleHR         | INT               | Throttle target hashrate in TH/s                                |                                                                                              | Y                      |
| Miner Mode         | INT               | Current miner mode (0 - Normal, 1 - Sleep, etc.)                | 0, 1, 2, 3, 4                                                                              | Y                      |
| Mining Mode        | INT               | Current mining mode (0 - Auto, 1 - Fixed)                       | 0, 1                                                                                        | Y                      |
| TargetHR           | INT               | User-set target hashrate for Auto mining mode                   |                                                                                              | Y                      |
| ShutDownTemp       | INT               | User-set critical temperature                                   |                                                                                              | Y                      |
| maxHrRestartAttempt| STRING            | Max attempts for HR restart before going to sleep              | Default value: 5                                                                            | Y                      |
| hrThreshold        | STRING            | Threshold for restarting if hashrate falls below this value    |                                                                                              | Y                      |
| maxErrRestart      | STRING            | Max attempts for error restart before sleeping                  |                                                                                              | Y                      |
| minFans            | STRING            | Minimum healthy fans to continue operation                       |                                                                                              | Y                      |
| pool1Port          | INT               | Port number for Pool 1                                          |                                                                                              | Y                      |
| pool1PW            | STRING            | Password for Pool 1                                            |                                                                                              | Y                      |
| pool2Port          | INT               | Port number for Pool 2                                          |                                                                                              | Y                      |
| pool2PW            | STRING            | Password for Pool 2                                            |                                                                                              | Y                      |
| pool3Port          | INT               | Port number for Pool 3                                          |                                                                                              | Y                      |
| pool3PW            | STRING            | Password for Pool 3                                            |                                                                                              | Y                      |
| Xcord              | STRING            | X coordinate of the miner's location                            |                                                                                              | Y                      |
| Ycord              | STRING            | Y coordinate of the miner's location                            |                                                                                              | Y                      |
| Zcord              | STRING            | Z coordinate of the miner's location                            |                                                                                              | Y                      |

> Note*: <br>
> All the parameters are fetched for each ASICs on all available hash boards in Miner whose count varies based on model. <br>
</details>

<details>
<summary>

<h4> GET summary.cgi </h4>

**Description:** Fetches Miner summary and ming status and other essential data for Dashboard.

</summary>

**End Point:** /cgi-bin/summary.cgi

**Parameters Required:** None.

**Response:**
```json
{
	"STATUS": [
		{
			"STATUS": "S",
			"When": 1719406139,
			"Code": 11,
			"Msg": "Summary",
			"Description": "BCFMiner 2.4.3 Test"
		}
	],
	"SUMMARY": [
		{
			"Elapsed": 12250,
			"GHS 5s": 137000,
			"GHS av": 135000,
			"GHS 30m": 136000,
			"Found Blocks": 0,
			"Getwork": 420,
			"Accepted": 793,
			"Rejected": 2,
			"Hardware Errors": 8,
			"Discarded": 56783,
			"Stale": 1,
			"Get Failures": 0,
			"Local Work": 56813,
			"Remote Failures": 0,
			"Network Blocks": 1,
			"Total MH": 137745488,
			"Work Utility": 0,
			"Difficulty Accepted": 2529323,
			"Difficulty Rejected": 0,
			"Difficulty Stale": 627693,
			"Best Share": 787387275,
			"Device Hardware%%": 0,
			"Device Rejected%%": 0,
			"Pool Rejected%%": 0,
			"Pool Stale%%": 0,
			"Last getwork": 1695624866
		}
	],
	"id": 1
}

```
**Parameter Specification Table**

-------------------------------------------------------------------------------------------------------------------------------------------------------
| Key               | Data Type          | Description                                                                                  | Supported by Foundry FW |
|-------------------|--------------------|----------------------------------------------------------------------------------------------|------------------------|
| STATUS            | STRING             | S - Success, F - Failure                                                                     | Y                      |
| When              | time_t or long int | Number of seconds elapsed since 00:00:00 hours, GMT (Greenwich Mean Time), January 1, 1970    | Y                      |
| Code              | INT                | Code that represents summary response (11)                                                  | Y                      |
| Msg               | STRING             | Describes the type of message                                                               | Y                      |
| Description       | STRING             | Describes the type of Firmware and its version                                              | Y                      |
| SUMMARY           |                    |                                                                                              |                        |
| Elapsed           | unsigned Int       | Miner uptime in seconds                                                                      | Y                      |
| GHS 5s            | INT                | Instantaneous hashrate in GH/s                                                              | Y                      |
| GHS av            | INT                | Last one hour average hashrate in GH/s                                                     | Y                      |
| GHS 30m           | INT                | Last 30 Min average hashrate in GH/s                                                       | Y                      |
| Found Blocks      | -                  | -                                                                                            | N                      |
| Getwork           | unsigned Int       | Total no of mining.notify or pool jobs received in current mining pool                       | Y                      |
| Accepted          | unsigned Int       | Total pool accepted shares in the current session                                          | Y                      |
| Rejected          | unsigned Int       | Total pool rejected shares in the current session                                          | Y                      |
| Hardware Errors   | unsigned Int       | Total no of Hardware Errors in the current session                                         | Y                      |
| Discarded         | -                  | -                                                                                            | N                      |
| Stale             | unsigned Int       | Total stale shares submitted to pool in the current session                                | Y                      |
| Get Failures      | -                  | -                                                                                            | N                      |
| Local Work        | -                  | -                                                                                            | N                      |
| Remote Failures   | -                  | -                                                                                            | N                      |
| Network Blocks    | -                  | -                                                                                            | N                      |
| Total MH          | Unsigned Int       | Instantaneous hashrate in TH                                                                | Y                      |
| Work Utility      | -                  | -                                                                                            | N                      |
| Difficulty Accepted| Unsigned Int       | Difficulty of the last pool accepted share                                                 | Y                      |
| Difficulty Rejected| Unsigned Int       | Difficulty of the last pool rejected share                                                 | Y                      |
| Difficulty Stale  | Unsigned Int       | Difficulty of the last stale share                                                         | Y                      |
| Best Share        | Unsigned Int       | Highest difficulty of the pool accepted share                                              | Y                      |
| Device Hardware%% | -                  | -                                                                                            | N                      |
| Device Rejected%% | -                  | -                                                                                            | N                      |
| Pool Rejected%%   | -                  | -                                                                                            | N                      |
| Pool Stale%%      | -                  | -                                                                                            | N                      |
| Last getwork      | -                  | -                                                                                            | N                      |
|                   |                    |                                                                                              |                        |
| id                | INT                | id of the message or priority of the message. Usually 1                                    | Y                      |

</details>


<details>
<summary>

<h4> GET getCpuStat.cgi </h4>

**Description: **Fetches the CPU Stats of the Miner controller.
This is similar to the “top” command in linux, which is used to monitor system stats and activity.

</summary>

**End Point:** /cgi-bin/getCpuStat.cgi

**Parameters Required:** None

**Response:**
```json
{
  "user": "0%",
  "sys": "4%",
  "nice": "0%",
  "idle": "95%",
  "iowait": "0%",
  "irq": "0%",
  "loadavg1Min": "0.37",
  "loadavg5Min": "0.99",
  "loadavg15Min": "0.72",
  "running processes": "1",
  "total processes": "113"
}
```
**Paramters Specification Table**

------------------------------------------------------------------------------------------------------------------------------------------------------
| Key                | Accepted Data Type | Description                                                                                                            | Valid Values | Supported by Foundry FW |
|--------------------|-------------------|------------------------------------------------------------------------------------------------------------------------|--------------|------------------------|
| "user"             | STRING            | Estimated percentage of CPU utilization at the user level (application level).                                         |              |                        |
| "sys"              | STRING            | Estimated percentage of CPU utilization at the system level (kernel level).                                            |              |                        |
| "nice"             | STRING            | Estimated percentage of CPU utilization executing processes with a positive nice value (low priority processes).       |              |                        |
| "idle"             | STRING            | Estimated percentage of CPU time spent idle (CPU not doing any work).                                                  |              |                        |
| "iowait"           | STRING            | Estimated percentage of CPU time spent waiting for I/O operations to complete.                                         |              |                        |
| "irq"              | STRING            | Estimated percentage of CPU time spent servicing hardware interrupts.                                                  |              |                        |
| "loadavg1Min"      | STRING            | System load average for the past 1 minute (average number of processes runnable or uninterruptable).                   |              |                        |
| "loadavg5Min"      | STRING            | System load average for the past 5 minutes.                                                                            |              |                        |
| "loadavg15Min"     | STRING            | System load average for the past 15 minutes.                                                                           |              |                        |
| "running processes" | STRING            | Number of processes currently running in the CB.                                                                       |              |                        |
| "total processes"  | STRING            | Total number of processes.                                                                                              |              |                        |

</details>

<details>
<summary>

<h4> GET getTimeZone.cgi </h4>

**Description:** Fetches the current timezone the system is configured to along with other available timezone.

</summary>
	
**End Point:**/cgi-bin/getTimeZone.cgi

**Parameters Required:** None

**Response: **

```json
{
    "timeZones": [
        {
            "name": "Africa/Johannesburg",
            "utcOffset": "+02:00"
        },
        {
            "name": "America/Chicago",
            "utcOffset": "-06:00"
        },
        {
            "name": "America/Denver",
            "utcOffset": "-07:00"
        },
        {
            "name": "America/Halifax",
            "utcOffset": "-04:00"
        },
        {
            "name": "America/Los_Angeles",
            "utcOffset": "-08:00"
        },
        {
            "name": "America/New_York",
            "utcOffset": "-05:00"
        },
        {
            "name": "America/St_Johns",
            "utcOffset": "-04:30"
        },
        {
            "name": "Asia/Kolkata",
            "utcOffset": "+05:30"
        },
        {
            "name": "Asia/Tokyo",
            "utcOffset": "+09:00"
        },
        {
            "name": "Australia/Sydney",
            "utcOffset": "+10:00"
        },
        {
            "name": "Europe/London",
            "utcOffset": "+01:00"
        },
        {
            "name": "Europe/Moscow",
            "utcOffset": "+03:00"
        },
        {
            "name": "Europe/Paris",
            "utcOffset": "+01:00"
        },
        {
            "name": "Pacific/Auckland",
            "utcOffset": "+12:00"
        },
        {
            "name": "Pacific/Honolulu",
            "utcOffset": "-10:00"
        },
        {
            "name": "UTC",
            "utcOffset": "+00:00"
        }
    ],
    "setTimeZone": [
        {
            "name": "UTC",
            "utcOffset": "+00:00"
        }
    ]
}

```

**Parameter Specification Table**

--------------------------------
|TimeZone           |utcOffset|
|-------------------|---------|
|Africa/Johannesburg|+02:0  |
|America/Chicago    |-06:00|
|America/Denver     |-07:00|
|America/Halifax    |-04:00|
|America/Los_Angeles|-08:00|
|America/New_York   |-05:00|
|America/St_Johns   |-04:30|
|Asia/Kolkata       |+05:30 |
|Asia/Tokyo         |+09:00|
|Australia/Sydney   |  +10:00|
|Europe/London      |+01:00 |
|Europe/Moscow      |+03:00  |
|Europe/Paris       |+01:00  |
|Pacific/Auckland   |+12:00  |
|Pacific/Honolulu   |-10:00|
|UTC                |+00:00 |
------------------------------------
</details>

<details>
<summary>

<h4> GET systemLogs.cgi </h4>

**Description:** Fetches Kernel level logs. Supported only for Foundry Controller Boards.

</summary>

**End Point:** /cgi-bin/systemLogs.cgi

**Parameters Required:** None.

**Response:**

```
[    0.000000] Booting Linux on physical CPU 0x0
[    0.000000] Linux version 5.4.31 (oe-user@oe-host) (gcc version 9.3.0 (GCC)) #1 SMP PREEMPT Tue Nov 2 07:05:34 UTC 2021
[    0.000000] CPU: ARMv7 Processor [410fc075] revision 5 (ARMv7), cr=10c5387d
[    0.000000] CPU: div instructions available: patching division code
[    0.000000] CPU: PIPT / VIPT nonaliasing data cache, VIPT aliasing instruction cache
[    0.000000] OF: fdt: Machine model: MYIR YA157C v2 www.myir-tech.com
[    0.000000] Memory policy: Data cache writealloc
.
.
.
.
```
</details>

<details>
<summary>

<h4> GET getDevFeeInfo.cgi </h4>

**Description:** Fetch the parameters related to Dev Fee.

</summary>

**End Point:**/cgi-bin/getDevFeeInfo.cgi

**Parameters Required:** None

**Response: **

```json
{
  "pool": "btc.foundryusapool.com",
  "port": "3333",
  "user": "btcfirmware1.C_9_btcfoundryu_ccc_S19JXPOEM24519",
  "pass": "x",
  "quota": "2.7"
}

```
</details>

<details>
<summary>

<h4> GET reboot.cgi </h4>

**Description:** Reboot the Miner.

</summary>

**End Point:** /cgi-bin/reboot.cgi

**Parameters Required:** None.

**Response:** No JSON Response. 

</details>

<details>
<summary>

<h4> GET getEepromData.cgi </h4>

**Description:** Fetches the EEPROM data from each hash board
 
</summary>

**End Point:**/cgi-bin/getEepromData.cgi

**Parameters Required:** None

**Response: **

```json
{
  "minerEepromArray": [
    {
      "Hashboard": 1,
      "EEPROM": "Read successfully",
      "HbInfoData": "HQDZYRCBDJABI17S8EDS1GM23BK25F1V22B3C1ALBHB56804HQDZ20240101001Y1",
      "BoardSerialNumber": "HQDZYRCBDJABI17S8",
      "ChipDie": "ED",
      "ChipMarking": "S1GM23BK25",
      "FtVersion": "F1V22B3C1",
      "ChipTech": "AL",
      "BoardName": "BHB56804",
      "FactoryJob": "QDZ20240101001Y1",
      "HbParamsData": "02 03 05 14 38 2A 27 0B 02 01 01 00 1D ",
      "Voltage": 1300,
      "Frequency": 515,
      "NonceRate": 9995,
      "PcbTempIn": 42,
      "PcbTempOut": 56
    },
    {
      "Hashboard": 2,
      "EEPROM": "Read successfully",
      "HbInfoData": "HQDZYRCBDJABI18SYEDJ1GB24ACCIF1V22B1C1RAGBHB56804HQDZ20240101001Y1",
      "BoardSerialNumber": "HQDZYRCBDJABI18SY",
      "ChipDie": "ED",
      "ChipMarking": "J1GB24ACCI",
      "FtVersion": "F1V22B1C1",
      "ChipTech": "RA",
      "BoardName": "BHB56804",
      "FactoryJob": "HQDZ20240101001Y1",
      "HbParamsData": "02 03 05 14 3B 2C 27 0E 02 01 01 00 0F ",
      "Voltage": 1300,
      "Frequency": 515,
      "NonceRate": 9998,
      "PcbTempIn": 44,
      "PcbTempOut": 59
    },
    {
      "Hashboard": 3,
      "EEPROM": "Read successfully",
      "HbInfoData": "HQDZYRCBDJABI17TWEDJ1GM22BP09F1V22B3C1ALBHB56804HQDZ20240101001Y1",
      "BoardSerialNumber": "HQDZYRCBDJABI17TW",
      "ChipDie": "ED",
      "ChipMarking": "J1GM22BP09",
      "FtVersion": "F1V22B3C1",
      "ChipTech": "AL",
      "BoardName": "BHB56804",
      "FactoryJob": "QDZ20240101001Y1",
      "HbParamsData": "02 03 05 14 3A 2B 27 08 02 01 01 00 19 ",
      "Voltage": 1300,
      "Frequency": 515,
      "NonceRate": 9992,
      "PcbTempIn": 43,
      "PcbTempOut": 58
    }
  ]
}

```

</details>

<details>
<summary>

<h4> GET  getVersion.cgi </h4>

**Description:** Fetches the version of the new online firmware update file (if available).
	
</summary>

**End Point:**/cgi-bin/getVersion.cgi

Parameters Required: None

**Response:**
```json
{"stats":"success","code":"V000","msg":"2.4.4"}
```

**Parameter Specification Table**

----------------------------------------------------------------------------------------------------
| Key   | Data Type | Description            | Valid Values            | Supported by Foundry FW |
|-------|-----------|------------------------|------------------------|------------------------|
| stats | STRING    | SUCCESS/ERROR          |                        | Y                      |
| code  | STRING    | V000/V001              |                        | Y                      |
| msg   | STRING    | No release file found/2.4.4 |                    | Y                      |
-----------------------------------------------------------------------------------------------------
</details>

<details>
<summary>

<h4> GET rebootLogs.cgi </h4>

**Description:** Fetches Reboot logs from miner

</summary>

**End Point:** /cgi-bin/systemLogs.cgi

**Parameters Required:** None.

**Response:** 
```
The file size is too large. Fetching only the last 20 lines. Download to view full data.
08/06/24 17:50:41	REBOOT from API:BTC
08/06/24 17:52:03	Exit due to NO POOL AVAILABLE FOR MINING
08/06/24 17:55:23	Exit due to HASHBOARD INITIALIZATION FAILED
08/07/24 10:27:38	Exit due to CRITICAL PARAMETER CHANGED
08/07/24 10:29:05	Exit due to NO POOL AVAILABLE FOR MINING
08/07/24 10:29:44	REBOOT from API:BTC
08/07/24 10:31:06	Exit due to NO POOL AVAILABLE FOR MINING
08/07/24 10:34:31	Exit due to NO POOL AVAILABLE FOR MINING
08/07/24 10:37:55	Exit due to NO POOL AVAILABLE FOR MINING
08/07/24 10:41:20	Exit due to NO POOL AVAILABLE FOR MINING
08/07/24 10:44:44	Exit due to NO POOL AVAILABLE FOR MINING
08/07/24 10:48:09	Exit due to NO POOL AVAILABLE FOR MINING
08/07/24 10:51:33	Exit due to NO POOL AVAILABLE FOR MINING
08/07/24 10:54:58	Exit due to NO POOL AVAILABLE FOR MINING
08/07/24 10:58:23	Exit due to NO POOL AVAILABLE FOR MINING
08/07/24 11:01:47	Exit due to NO POOL AVAILABLE FOR MINING
08/07/24 11:05:12	Exit due to NO POOL AVAILABLE FOR MINING
08/07/24 11:05:24	REBOOT from API:BTC
08/07/24 11:06:46	Exit due to NO POOL AVAILABLE FOR MINING
08/07/24 11:10:06	Exit due to HASHBOARD INITIALIZATION FAILED
```
</details>

<details>
<summary>

<h4> GET getError.cgi </h4>

**Description:** Fetches  the Miner errors if available.

</summary>

**End Point: **/cgi-bin/getError.cgi

**Parameters Required:** None.

**Response:**

```json
{
  "errors": []
}
```
**Parameter Specification Table**

----------------------------------------------------------------------------------------------------------------------------------
|Key            |Data-Type|Info    |Valid Values | Supported <br> by <br>Foundry FW |
|---------------|------------------|-----------|----------------|---------------------|
|timestamp      |STRING            |Timestamp of the critical error message. will be "null" if there are no critical errors.|      |       Y            |
|errNo          |STRING            |Error no of thecritical error. Will be "null' if there are no critical errors| | Y |
|msg            |STRING            |Description of the critical error. Will be "null" if there are no errors| |Y |
                                        
---------------------------------------------------------------------------------------------------------------------------------
</details>

<details>
<summary>

<h4> GET get_blink_status.cgi </h4>

**Description:** gets LED blinking status. Responds boolean false (if not blinking) or true (if blinking).

</summary>

**End Point:**/cgi-bin/get_blink_status.cgi

**Parameters Required:** None

**Response:** 
```json
{"blink":false}
```
**Parameter Specification Table**

---------------------------------------------------------------------------------------------------------------------------------
|Key        | Data-Type|Info|Valid Values   |Spported<br> by <br>Foundry FW                                        |
|-----------|------------------|-----------|----------------|---------------------------------------------------------------|
|blinkStatus|bool              |Current level of blinkStatus <br> 1. false  For locateOff    <br>  2. true For locateOn|                |                                   Y                            |
---------------------------------------------------------------------------------------------------------------------------------

</details>

<details>
<summary>

<h4> GET resetAndCheck.cgi </h4>

**Description:** This cgi checks if latest FW for online update is available and updates it automatically if the auto update flag is true
	
</summary>

**End Point:**/cgi-bin/resetAndCheck.cgi

**Parameters Required:** None

**Response:**
```json
{
    "stats": "success",
    "code": "U001",
    "msg": "Update Successfull!"
}

```
</details>

</details>

<details>
<summary>
<h3> POST Commands <h3>

</summary>

<details>
<summary>

<h4> POST blink.cgi </h4>

**Description:** Locate Miner By blinking LEDs and Sounding Buzzer for Ten Minutes.
	
</summary>

**End Point:**/cgi-bin/blink.cgi

**Parameters Required:** <br>
true : to turn ON blinking <br>
false : to turn OFF blinking <br>

**Request:**
```json
{"blink":"user-input"}
```
</details>

<details>
<summary>

<h4> POST reset_conf.cgi </h4>

**Description:** Resets all the configuration settings.
	
</summary>

**End Point:**/cgi-bin/reset_conf.cgi

**Parameters Required:** <br>
true : to turn ON blinking <br>
false : to turn OFF blinking <br>

**Request:** <br>
No Request - The settings gets reset once the cgi is called

**Response:**
```json
{"stats":"success","code":"U001","msg":"null"}
```
</details>


<details>
<summary>

<h4> POST configMiner.cgi </h4>

**Description:** These sets of requests are used to set Crucial Mining Parameters.
	
</summary>

**End Point:**/cgi-bin/configMiner.cgi

**Parameters Required:** <br>
> NOTE:<br>
> The Request JSON should contain only the command’s value and parameter’s value as shown below,
> ``` 
> {“fanOverride”:“0”}
> ```
> The Cgi automatically parses this to the standard format.
> ```	
> i.e., {“command” : “fanOverride”, “parameter” : “0”}
> ```

<details>
<summary>
<h5> Fan Over-ride</h5>

**Description:** Changes the fan mode.
</summary>

**Request:** <br>
```json
{"fanOverride":"user-input"}
```

**Parameters:**<br>
Replace “user-input” in request to required parameter as shown below:<br>
0 - Auto Fan mode <br>
1 - Immersion mode <br>
2 - Fan Manual mode <br>
</details>

<details>
<summary>
<h5> Target Hashrate </h5>

**Description:** Modifies the target hash rate to set value in Auto Mining Mode.
</summary>

**Request:** <br>
```json
{"targetHashrate":"user-input"}
```

**Parameters:**<br>
Replace “user-input” in request to required integer value.<br>
Prescribed Value - <br>
20-170 for the miners in air cooled mode. <br>
20 -300 for the miners in immersion cooling mode. <br>
>Note: <br>
>Miner should be running in advanced work mode to post this command <br>
</details>

<details>
<summary>
<h5> Mining Mode </h5>

**Description:** Modifies the Mining Mode.
</summary>

**Request:** <br>
```json
{"mode":"user-input"}
```

**Parameters:**<br>
Replace “user-input” in request to required parameter as shown below:<br>
0 - Auto mining mode <br>
1- Fixed mining mode <br>

</details>

<details>
<summary>
<h5> Set Miner Model </h5>

**Description:** Modifies the Miner-model of the machine.
</summary>

**Request:** <br>
```json
{"setMinerModel":"user-input"}
```

**Parameters:**<br>
Replace “user-input” in request to required parameter as shown below:<br>
 -1 - Trigger miner detection <br>
 0 - S19 <br>
 1 - S19j Pro <br>
 2 - S19 XP <br>
 3 - S19j Pro with PIC <br>
 4 - S19 with 126 ASICs <br>
 5 - S19k Pro <br>

</details>

<details>
<summary>
<h5> Set Voltage </h5>

**Description:** Modifies the Voltage delivered to Hashboards in Fixed Mining Mode
</summary>

**Request:** <br>
```json
{"setVoltage":"user-input"}
```

**Parameters:**<br>
Replace “user-input” in request to required Voltage Value. <br>
Any Value within 12V to 17V is accepted based on the PSU version used by the miner. <br>
>NOTE:<br>
>For setting the voltage as 12V, the parameter should be 120,Similarly for setting the voltage as 15.1V, the parameter should be 151 and so on.<br>

</details>

<details>
<summary>
<h5> Set Frequecy </h5>

**Description:** Modifies the Clock Frequency of the ASICs on Hashboards, in Fixed Mining Mode

</summary>

**Request:** <br>
```json
{"setFrequency":"user-input"}
```

**Parameters:**<br>
Replace “user-input” in request to required Frequency Value in Integer. <br>
Any Integer Value within 0Hz -1000MHz is accepted. <br>

</details>

<details>
<summary>
<h5> HB1 Enable </h5>

**Description:** Enables or Disables Hash Board 1.
</summary>

**Request:** <br>
```json
{"HB1Enable":"user-input"}
```

**Parameters:**<br>
Replace “user-input” in request to:<br>
true - to enable the Hashboard <br>
false - to disable the Hashboard <br>

</details>

<details>
<summary>
<h5> HB2 Enable </h5>

**Description:** Enables or Disables Hash Board 2.
</summary>

**Request:** <br>
```json
{"HB2Enable":"user-input"}
```

**Parameters:**<br>
Replace “user-input” in request to:<br>
true - to enable the Hashboard <br>
false - to disable the Hashboard <br>

</details>

<details>
<summary>
<h5> HB3 Enable </h5>

**Description:** Enables or Disables Hash Board 3.
</summary>

**Request:** <br>
```json
{"HB3Enable":"user-input"}
```

**Parameters:**<br>
Replace “user-input” in request to:<br>
true - to enable the Hashboard <br>
false - to disable the Hashboard <br>

</details>

<details>
<summary>
<h5> Add Pool </h5>

**Description:** Add new Pool to the existing Pools.
</summary>

**Request:** <br>
```json
{
"command" : "addpool" , 
"parameter" :"[poolURL:port] , [workername],[password],[index]" 
}
```

**Parameters:**<br>
- poolURL:port Pool : URL and port number are entered in the same format.<br>
> Note: stratum+tcp not to be included in the URL.<br>
- [workername] : Worker name of the miner.<br>
- [password] : Pool Password.<br>
- [index]: Priority of the pool that is being added is entered here, this field is not mandatory.<br>

</details>

<details>
<summary>
<h5> Target Chip Temperature </h5>

**Description:** Modify the critical/shutdown temperature of the miner.
</summary>

**Request:** <br>
```json
{"setTargetChipTemp":"user-input"}
```

**Parameters:**<br>
Replace “user-input” in request to any value between 40 - 90. <br>

</details>

<details>
<summary>
<h5> Fan Speed </h5>

**Description:**  Modify the fan speed when fans are running in Manual Mode.
</summary>

**Request:** <br>
```json
{"setManualFanSpeed":"user-input"}
```

**Parameters:**<br>
Replace “user-input” in request to any value between 0 - 100 in string format.<br>
</details>

<details>
<summary>
<h5> Modify Pools </h5>

**Description:** Modify the existing pool configuration.
</summary>

**Request:** <br>
```json
{
    "command": "modifyPools",
    "parameter": [
        {
            "address": "btc.foundryusapool.com",
            "password": "X",
            "port": 3333,
            "username": "ccc.S19JPRO_15"
        },
        {
            "address": "btc.foundryusapool.com",
            "password": "X",
            "port": 443,
            "username": "ccc.S19JPRO_15"
        },
        {
            "address": "btc.foundryusapool.com",
            "password": "X",
            "port": 25,
            "username": "ccc.S19JPRO_15"
        }
    ]
}
```

**Parameters:**<br>
"address": Pool address or URL<br>
"password": Respective Pool Password <br>
"port": Port number for pool communications <br>
"username": Username <br>
>NOTE:<br>
>All parameters should be given in “string” data type in JSON format.

</details>

<details>
<summary>
<h5> Miner Mode </h5>

**Description:** Modify the Miner Mode.
</summary>

**Request:** <br>
```json
{“setMinerMode":"user-input"}
```

**Parameters:**<br>
“0” - Normal Mode <br>
“1” - Sleep Mode <br>
“2” - High Energy Mode <br>
“3” - Low Power Mode <br>
“4” - Advanced Mode <br>
>NOTE:<br>
>All parameters should be given in “string” data type in JSON format.

</details>

</details>

<details>
<summary>
<h4> POST deleteLogs.cgi </h4>

**Description:** Deletes the older logs except for present and previous days logs (both csv and text files will be deleted).
</summary>

**End Point:** /cgi-bin/deleteLogs.cgi

**Request:** <br>
```json
{
    "logs": [List_of_logs_to_be_deleted],
    "csv": [List_of_csv_to_be_deleted]
}
```

**Parameters:**<br>
Log File names<br>

**Response:**
```
03/28/25 15:22:48 Block Found Diff 1288607092084618.8/113757508810854.0
```

</details>

<details>
<summary>
<h4> POST setDefaultName.cgi </h4>

**Description:** When called, sets the host name of the miner to standard nomenclature (i.e., foundry-<MAC address>)
</summary>

**End Point:** /cgi-bin/setDefaultName.cgi

**Request:** <br>
NA

**Parameters:** None

**Response:**
```json
{
  "stats": "success",
  "code": "P000",
  "msg": "Success: Default Hostname set!"
}
```

</details>

<details>
<summary>
<h4> POST setTimeZone.cgi </h4>

**Description:** Changes the system timezone. 
</summary>

**Available Timezones:**
| TimeZone             | UTC Offset |
|----------------------|------------|
| Africa/Johannesburg  | +02:00     |
| America/Chicago      | -06:00     |
| America/Denver       | -07:00     |
| America/Halifax      | -04:00     |
| America/Los_Angeles  | -08:00     |
| America/New_York     | -05:00     |
| America/St_Johns     | -04:30     |
| Asia/Kolkata         | +05:30     |
| Asia/Tokyo           | +09:00     |
| Australia/Sydney     | +10:00     |
| Europe/London        | +01:00     |
| Europe/Moscow        | +03:00     |
| Europe/Paris         | +01:00     |
| Pacific/Auckland     | +12:00     |
| Pacific/Honolulu     | -10:00     |
| UTC                  | +00:00     |


**End Point:** /cgi-bin/setTimeZone.cgi

**Request:** <br>
```json
{"zone": "UTC"}
```

**Parameters:** Timezone

**Response:**
```json
{"stats":"success","msg":"Time Zone set to UTC"}
```

</details>

<details>
<summary>
<h4> POST set_legacy_mode.cgi </h4>

**Description:**  sets the legacy mode configuration to true or false.<br>
“0” - False <br>
“1” - False <br>

</summary>

**End Point:** /cgi-bin/set_legacy_mode.cgi

**Request:** <br>
```json
{"legacyMode":1} 
```

**Parameters:** <br>
“0” - False <br>
“1” - False <br>

**Response:**
```json
{"legacyMode":1} 
```

</details>

<details>
<summary>
<h4> POST  getNsLookup.cgi </h4>

**Description:** Makes Nslookup linux tool available to users to map IPs to DNS.

</summary>

**End Point:** /cgi-bin/getNsLookup.cgi

**Request:** <br>
```json
{"IP":"","networkTool":"2"}
```

**Parameters:** <br>
“IP”: Ip Address to be probed. <br>
"networkTool": Enter Network Tool Identification code as 2 <br>	

**Response:**
```
Name: 1.1.1.1
Address 1: 1.1.1.1 one.one.one.one
```

</details>

<details>
<summary>
<h4> POST set_miner_conf.cgi </h4>

**Description:** Configures Pool information, Miner Modes.
</summary>

**End Point:** /cgi-bin/set_miner_conf.cgi

**Request:** <br>
```json
{
    "bitmain-fan-ctrl": true,
    "bitmain-fan-pwm": "10",
    "freq-level": "70",
    "miner-mode": 1,
    "pools": [
        {
            "pass": "123",
            "url": "stratum+tcp://btc.foundryusapool.com:3333",
            "user": "ccc.S19XP_B1"
        },
        {
            "pass": "123",
            "url": "stratum+tcp://btc.foundryusapool.com:443",
 
           "user": "ccc.S19XP_B1"
        },
        {
            "pass": "123",
            "url": "stratum+tcp://btc.foundryusapool.com:25",
            "user": "ccc.S19XP_B1"
        }
    ]
}
```

**Parameters:** <br>
 - Supported Miner Mode parameters: <br>
    0 - Normal Mode <br>
    1 - Sleep Mode <br>
    2 - High Energy Mode <br>
    3 - Low Power Mode <br>
    4 - Advanced Mode <br>
 - Pools parameters: <br>
   “pass” : Pool password <br>
   “url” : Pool URL <br>
   “user”: User Name <br>

>Note: Only above mentioned parameters are currently supported to configure.

</details>

<details>
<summary>
<h4> POST  set_network_conf.cgi </h4>

**Description:** Modify network configuration for DHCP or static IP.
</summary>

**End Point:** /cgi-bin/set_network_conf.cgi

**Request:** <br>
```json
{"ipPro":2,"ipHost":"ip120v2","ipAddress":"192.168.0.120","ipGateway":"192.168.0.1","ipDns":"8.8.8.8","ipSub":"255.255.255.0"}
```

**Parameters:** <br>
- For static IP: <br>
   "ipPro":”2” for static. <br>
   "ipHost": Hostname to be configured.<br>
   "ipAddress":User requested IP address in Static configuration.<br>
   "ipGateway": User requested gateway in Static configuration.<br>
   "ipDns": User requested DNS Server in Static configuration.<br>
   "ipSub": User requested Subnet mask in Static configuration.<br>
- For DHCP IP:<br>
   "ipPro": “1” for DHCP.<br>
   "ipHost": Hostname to be configured.<br>

**Response:**
```json
{"stats":"success","code":"N000","msg":"OK!"}
```

</details>

<details>
<summary>
<h4> POST  getPing.cgi </h4>

**Description:** Pings the server to check the connectivity
</summary>

**End Point:** /cgi-bin/getPing.cgi

**Request:** <br>
```json
{"IP":"" ,"networkTool":"1"}
```

**Parameters:** <br>
“IP”: Ip Address to be probed. <br>
"networkTool": Enter Network Tool Identification code as 1 <br>	

**Response:**
```
PING 1.1.1.1 (1.1.1.1) 56(84) bytes of data.
64 bytes from 1.1.1.1: icmp_seq=1 ttl=48 time=19.6 ms
64 bytes from 1.1.1.1: icmp_seq=2 ttl=48 time=19.7 ms
64 bytes from 1.1.1.1: icmp_seq=3 ttl=48 time=19.6 ms
--- 1.1.1.1 ping statistics
--- 3 packets transmitted, 3 received, 0% packet loss, time 2003ms rtt min/avg/max/mdev = 19.550/19.600/19.654/0.042 ms
```

</details>

<details>
<summary>
<h4> POST  passwd.cgi </h4>

**Description:** Reset the GUI/Web application password and User name.
</summary>

**End Point:** /cgi-bin/passwd.cgi

**Request:** <br>
```json
{
"username":"",
"curPwd":"",
"newPwd":"",
"confirmPwd":""
}
```

**Parameters:** <br>
“username”: New User name to be updated/ current username(Not a mandatory field). <br>
”curPwd”: Old password currently in use <br>
”newPwd”:New password to be set <br>
”confirmPwd”: New password re entry for confirmation. <br>

**Response:**
```json
{
 stats":"success",
"code":"P000",
"msg":"OK!"
}
```

</details>

<details>
<summary>
<h4> POST set_ntp_server.cgi </h4>

**Description:** Configures the NTPs to user set servers
</summary>

**End Point:** /cgi-bin/set_ntp_server.cgi

**Request:** <br>
```json
{
      "ntpServer0":"",
      "ntpServer1":"",
      "ntpServer2":""
}
```

**Response:**
```json
{
    "stats":"success",
    "code":"N000" , 
    "msg":"URL or IP you provided are set as ntp and backup ntp server"
}
```

</details>

<details>
<summary>
<h4> POST  reIdentify.cgi </h4>

**Description:** To reidentify the miner model of the machine.
</summary>

**End Point:** /cgi-bin/reIdentify.cgi

**Request:** <br>
```json
{"reIdentifyMiner":"-1"}
```

**Parameters:** None

**Response:**
```json
{"status":"success","message":"null"}
```
</details>

<details>
<summary>
<h4> POST  getTraceRoute.cgi </h4>

**Description:** Provides a map of how data on the internet travels from its source to its destination
</summary>

**End Point:** /cgi-bin/getTraceRoute.cgi

**Request:** <br>
```json
{"IP":"" ,"networkTool":"3"}
```

**Parameters:** <br>
“IP”: Ip Address to be probed.<br>
"networkTool": Enter Network Tool Identification code as 3 <br>

**Response:**
```
traceroute to 8.8.8.8 (8.8.8.8), 30 hops max, 38 byte packets
1 _gateway (10.2.30.1) 0.245 ms 0.223 ms 0.192 ms
2 ve164.br01.erch.fibertech.com (69.195.47.97) 0.477 ms 0.656 ms 0.545 ms
3 144.121.109.147.lightower.net (144.121.109.147) 3.043 ms 2.872 ms 2.695 ms
4 160.72.249.214.lightower.net (160.72.249.214) 3.516 ms 3.533 ms 3.229 ms
5 160.72.252.112.lightower.net (160.72.252.112) 6.760 ms 5.797 ms 5.609 ms
6 160.72.252.111.lightower.net (160.72.252.111) 6.108 ms 5.760 ms 5.752 ms
7 160.72.252.45.lightower.net (160.72.252.45) 7.724 ms 7.689 ms 7.777 ms
8 ae11-nwrknjmdjp1.lightower.net (104.207.214.66) 9.962 ms 9.616 ms 9.620 ms
9 ae10-nwrknjmdj92.lightower.net (144.121.35.236) 9.554 ms 9.562 ms 9.526 ms
10 192.178.70.182 (192.178.70.182) 9.577 ms 9.657 ms 9.692 ms
11 192.178.107.21 (192.178.107.21) 10.360 ms 192.178.106.111 (192.178.106.111) 10.755 ms 10.925 ms
12 142.250.235.239 (142.250.235.239) 10.875 ms 216.239.49.65 (216.239.49.65) 10.175 ms 142.251.60.179 (142.251.60.179) 10.271 ms
13 dns.google (8.8.8.8) 10.169 ms 9.928 ms 10.172 ms
```
</details>

<details>
<summary>
<h4> POST uninstall.cgi </h4>

**Description:** Uninstalls FDOS from the miner.
</summary>

**End Point:** /cgi-bin/uninstall.cgi

**Request:** <br>
NA

**Parameters:** None

**Response:** <br>
NA

</details>

<details>
<summary>
<h4> POST setDefaultName.cgi </h4>

**Description:** Uninstalls FDOS from the miner.
</summary>

**End Point:** /cgi-bin/setDefaultName.cgi

**Request:** <br>
NA

**Parameters:** None

**Response:**
```json
{
  "stats": "success",
  "code": "P000",
  "msg": "Success: Default Hostname set!"
}
```

</details>

<details>
<summary>
<h4> POST upgrade.cgi </h4>

**Description:** Update files are provided with .tar.gz extensions, they can be used in GUI , btcTools and also with this API.
</summary>

**End Point:** /cgi-bin/upgrade.cgi

**Request:** <br>
NA

**Parameters:** <br>
Upload file with format ‘.tar.gz’ <br>

**Response:**
```json

```

</details>
</details>
