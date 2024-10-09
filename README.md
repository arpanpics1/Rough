Hi [Recipient's Name],

I wanted to provide you with an update regarding the ARC testing we performed on the EEH cluster on October 27th, as part of our annual reliability check. The goal was to move applications from the VA cluster to the TX Data Center.

During the testing, all producer applications were successfully migrated from VA to TX. However, when we moved the consumers for the related topics to the TX Data Center, we encountered an issue due to a human error. The consumer migration was supposed to be done using the CST time zone, but instead, GMT was used, which led to the problem.

Fortunately, this issue had already been identified earlier, and we worked closely with the team, particularly Lakshmi Kota, to resolve it. As mentioned in the attached email, the data has been restored and moved to the required location.

Please let me know if you need any further details or clarifications.

Best regards,
[Your Name]


