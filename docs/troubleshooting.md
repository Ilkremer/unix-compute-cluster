## Windstream T3200 Troubleshooting

### Initial Problem
The T3200 was tested as a possible low-cost switch/router for the cluster network, but Ethernet connectivity was unstable and links repeatedly dropped.

### Investigation
Troubleshooting initially focused on link stability, cabling, and device behavior. During that process, I discovered that one of the power adapters used for testing did not match the device's required power specifications. A later adapter change introduced an incorrect voltage, after which the unit showed signs of electrical damage.

### Conclusion
Because the T3200 could no longer be considered a reliable test platform, and because further diagnosis would likely require board-level electronics troubleshooting/repair, I decided not to continue using it for this project.

### Resolution
I replaced the T3200 approach with a dedicated Ethernet switch, which is a simpler and more reliable solution for the cluster network backbone.

### Lessons Learned
- Always verify voltage, current, polarity, and connector compatibility before powering hardware
- Separate network troubleshooting from power-related troubleshooting when diagnosing unstable devices
- Replacing a damaged low-value component can be more practical than pursuing deep repair when it is outside the project's scope