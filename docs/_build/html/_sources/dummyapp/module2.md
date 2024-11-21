# Module 2: Sending Data from DummyApp

## Overview

**What is Module 2?**

Module 2 allows users to retrieve and send data from the DummyApp database to external systems or services. It includes functionalities for exporting tasks, users, or reports, as well as sending data via APIs or file formats.

--

### Configuration Options

The following configurations are available for Module 2:

| Field Name         | Description                               | Type     | Default   | Required/Optional |
|--------------------|-------------------------------------------|----------|-----------|-------------------|
| Export Format      | The format to export data (e.g., JSON).   | string   | JSON      | Required          |
| API Endpoint       | The endpoint to send the data.            | string   | None      | Required          |
| Timeout            | Timeout for sending data in seconds.      | int      | 30        | Optional          |
| Authentication Key | Key for authenticating the API call.      | string   | None      | Required          |

---
