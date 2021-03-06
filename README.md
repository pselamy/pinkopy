pinkopy
=======

[![Build Status](https://travis-ci.org/theherk/pinkopy.svg)](https://travis-ci.org/theherk/pinkopy)

pinkopy is a Python wrapper for the Commvault api. Of course it does very little initially, but there is no reason to duplicate work across projects.

Installation
------------

    git clone git@github.com:theherk/pinkopy.git
    pip install pinkopy

Usage
-----

```python
from pinkopy import CommvaultSession

config = {
    'service': 'service url',
    'user': 'username',
    'pw': 'password'
}

with CommvaultSession(**config) as s:
    client_jobs = s.get_jobs('1234', job_filter="Backup")
    cust_jobs = s.get_subclient_jobs(client_jobs, '12345678', last=3)
    # multi status
    for job in cust_jobs:
        job_id = job['jobSummary']['@jobId']
        job_details = s.get_job_details('1234', job_id)
        job_vmstatus = s.get_job_vmstatus(job_details)
```

Contribution
------------

Please do contribute to this repository. It currently only supports a small set of the api provided by Commvault. However, if you do contribute, please follow these guidelines.

### Guidelines

+ Use [Gitflow](https://www.atlassian.com/git/tutorials/comparing-workflows/). Your pull requests must come from a Gitflow branch.
    - feature/yourfeature
    - bugfix/issuenumber
+ **ONLY** imperative commit messages. Line one is one imperative, brief sentence. Following lines may have more details.
+ Builds must pass (which should be pretty easy right now, since there are no tests).
+ Never commit binary files.
+ Make sure you are committing with your Github user.

---

#### Name

The name was originally going to be commpy, but then I liked commiepy. From here it was only a small leap to pinkopy, a tribute to a dear friend of mine.

<img src="http://i.imgur.com/gAs94pn.png" alt="Pinkie Pie" width="200">
