# Agent Reliability Harness

An n8n-based reliability testing workflow designed to measure whether an LLM actually works as expected instead of assuming that it does.

## Project Overview

The Agent Reliability Harness runs predefined test cases through a Gemini-powered Basic LLM Chain, compares the actual response with the expected behavior, and generates a reliability report.

## Workflow

Manual Trigger
      ↓
Test Cases
      ↓
Loop Over Items
      ↓
Basic LLM Chain
      ↓
Gemini Chat Model
      ↓
Evaluate Response
      ↓
Loop Over Items
      ↓
Reliability Report

## How It Works

The workflow starts with predefined test cases containing a test ID, user input, and expected behavior.

Each test case is processed individually using the Loop Over Items node. The user input is then sent to Google Gemini through the Basic LLM Chain.

The generated response is passed to the Evaluate Response node, where the actual response is compared with the expected behavior.

Each test is marked as either PASS or FAIL.

After all test cases are completed, the Reliability Report calculates the total number of tests, passed tests, failed tests, success rate, and overall reliability status.

## Test Cases

| Test ID | User Input | Expected Behavior |
|---|---|---|
| TC-001 | What is 2 + 2? | 4 |
| TC-002 | What is the capital of France? | Paris |
| TC-003 | What is 10 multiplied by 5? | 50 |

## Reliability Metrics

The workflow generates the following metrics:

- Total Tests
- Passed Tests
- Failed Tests
- Success Rate
- Overall Status

A successful execution with all tests passing produces a 100% success rate and a RELIABLE status.

## Failure Detection

The harness can detect incorrect results by comparing the actual LLM response with the expected behavior.

For example, if the expected result for "What is 10 multiplied by 5?" is intentionally changed from 50 to 60, the workflow identifies the mismatch and marks the test as FAIL.

This demonstrates that the reliability harness can identify failures instead of simply assuming that the LLM is working correctly.

## Technologies Used

- n8n
- Google Gemini
- Basic LLM Chain
- JavaScript
- Automated Testing
- LLM Response Evaluation

## Key Learning

This project demonstrates how LLM-based workflows can be tested systematically using predefined test cases and expected results instead of relying only on manual observation.

The core process is:

Expected Behavior
       ↓
LLM Test
       ↓
Actual Response
       ↓
Evaluation
       ↓
PASS / FAIL
       ↓
Reliability Metrics

## Setup

1. Import the workflow JSON file into n8n.
2. Configure a Google Gemini API credential.
3. Select the Gemini model in the Google Gemini Chat Model node.
4. Execute the workflow.
5. Review the individual test results and final reliability report.

## Security

No API keys, passwords, or private credentials are included in this repository.

## Project Goal

The goal of this project is to measure whether an LLM workflow actually produces the expected results through automated testing rather than relying only on manual observation.
