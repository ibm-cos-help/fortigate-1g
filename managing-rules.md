---

copyright:
  years: 2017
lastupdated: "2017-11-29"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}

# Manage Firewall Rules (Policies)

FortiGate utilizes the concept of a "policy", which includes the ability to accept/deny traffic, apply security profiles, shape traffic, log traffic, and schedule a timeframe for a policy to apply. To assemble a policy, you must first create the objects that will take part in it. 

1. Log into the appliance using the credentials found in the **Device Details** page in the [Customer Portal ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://control.softlayer.com/){: new_window}. Follow the How to [Manage the FortiGate Security Appliance](managing-fsa.html) instructions to find the credentials.
2. After logging into the appliance, navigate to the **Policy and Objects** menu and select the protocol you wish to manage (such as IPv4 or IPv6). Policies are implemented against traffic based on the Sequence Number on the far left. Users can drag a policy higher in the list to have it implemented earlier or vice versa.
3. To add a policy, click **Create New** and refer to these field definitions:

    **Incoming Interface:** Either the public-facing interface (outside interface) for ingress rules or compute-facing interface (inside interface) for egress rules.

    **Source Address:** This is the source IP(s) for the traffic. The IP must be added to the "Addresses" list on the "Objects Menu." Note that an "All" option is available.

    **Source User(s):** This applies the policy to a user or group created in the "User and Device" panel.

    **Source Device Type:** This applies the policy to a device created in the "User and Device" panel.

    **Destination Address:** This is the target IP(s) of the traffic. The IP must be added to the "Addresses" list on the "Objects Menu." Note that an "All" option is available.

    **Schedule:** This determines when the policy will run. An "Always" option is available. You can also create a schedule in the Objects menu under Schedules.

    **Service:** This determines the service that the policy will apply to. An "ALL" option is available as well as numerous standard services. Additional services can be added in the Services menu under Objects.

    **Action:** Accepts or denys the traffic. 

    **Firewall / Network Options:** Enables or disables NAT and its associated options.

    **Security Profiles:** Provides an On/Off toggle for each option, as well as allows association to the profile.

    **Traffic Shaping:** This allows you to configure the maximum and guaranteed (minimum) bandwidth available to the traffic. A maximum connections limit can also be set on a per-IP shaper. 

    DSCP settings are not effective since user generated QoS information is ignored by the IBM Cloud platform.

    **Logging Options:** Configures when "Allowed" traffic is recorded. This setting (and especially the "Capture Packets" option) utilize device resources.

    **Comments:** User generated comments

    **Enable this policy:** Enables or disables the policy

## Example of a simple "Allow All" rule for web traffic to a web server

***Incoming Interface:*** *outside VLAN*

***Source Address:*** *All*

***Source User(s):** *Blank*

***Source Device Type:*** *Blank*

***Outgoing Interface:*** *inside VLAN*

***Destination Address:*** *x.x.x.x (Web Server IP)*

***Schedule:*** *always*

***Service:*** *HTTP*

***Action:*** *ACCEPT*

***NAT:*** *OFF*

***Security Profiles:*** *Use Standard*

***Traffic Shaping:*** *Off*

***Log Allowed Traffic:*** *On (Security Events)*

***Comments:*** *Web Server Traffic x.x.x.x*

***Enable this policy:*** *On*
