# AWS Cloud Cost Optimization — Identifying Stale EBS Snapshots

## Overview
This project demonstrates **AWS Cloud Cost Optimization** by identifying and cleaning up **stale EBS snapshots** that are no longer associated with any active EC2 instance.  

The main goal is to **reduce unnecessary storage costs** by removing snapshots that are not in use.  

---

## Description
The project uses a **Python Lambda script** to manually identify stale EBS snapshots:

- Fetches all EBS snapshots owned by the account (`self`).  
- Retrieves a list of active EC2 instances (running or stopped).  
- Checks each snapshot to see if the associated volume is not attached to any active instance.  
- Deletes the snapshot if it is stale, effectively optimizing storage costs.  

> ⚠️ In this project, the cleanup is **executed manually**, but the same script can be scheduled using **CloudWatch Events / EventBridge** for automatic cleanup.

---

## How it Works
1. Run the Python script (`lambda_snapshot_cleanup.py`) manually.  
2. The script identifies snapshots that are not associated with any active EC2 instance.  
3. It deletes these stale snapshots and outputs logs in the console.  
4. Storage costs are reduced by cleaning unused snapshots.

---

## Usage
1. Ensure you have **Python 3** and **Boto3** installed.  
2. Configure your **AWS credentials** locally (`aws configure`).  
3. Run the script:


