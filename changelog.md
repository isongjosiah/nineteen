# 4.0

## 🚀 High Level Flow Changes
- Validators will auto adjust to maximize the capacity of a miner on 60-min intervals 🚀
- Miners can chose to rate limit by adjusting their task config files (be careful with your HTTP 429s 🛑)
- Dropped Finetune for now 👋
- Dropped GoAPI SOTA API requirement (savings here) 🫡
- Miners will have massively increased visibility onto their performance through dashboards 🔥

## Scoring overview
-  Validators synthetically score miners on these requests, calculating a `period_score`, which represents reliability.
-  Validators workflow for each task:
     - Use the quality scores calculated from the scoring of all tasks for this UID, with a preference for quality scores from this specific task.
     - Use a decaying weighted average of previous period scores to calculate a weighted period score.
     - Combine the weighted period score with the task quality score and multiply by volume to get the effective volume (capacity).
     - Compare the effective capacities with others to get a score for this UID for the task.
     - Weight all scores across each task using the subnet-level task weights to derive an overall incentive score.
     - Miners can rate limit explicitly to validators without incurring a greater penalty, depending on volume.


## 🆙 Upgrades
-    Bittensor upgrade to version 6.9.3.

## 🔧 Validator Enhancements
-    Validators to store extensive stats information.
-    Reworked weight setting to utilize announced capacities and 'evidence' of those capacities.
-    Increased range for speed scores.
-    Posted stats for sexy dashboards.
-    Small bug fixes for validator proxy.
-    Implemented smart load balancing between miners for organic requests using a doubly linked list.
-    Cleaned up outdated code.
-    Separated validator into specific duties.