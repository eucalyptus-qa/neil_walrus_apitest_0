neil_walrus_apitest_0
=====================

## Description

Ensure the API compatibility between S3 and Walrus

## Procedure

1. Create a bucket using RightAws::S3::Bucket API in a particular location 'US'
2. Create 50 objects with 'test_object_' as a prefix
3. Check that the bucket.keys('prefix' ⇒ 'test_') returns 50 keys
4. [FAIL] Not the right number of objects returned
5. [IMPROVE]Should also add different objects to make sure the entire bucket isnt being returned
6. Delete objects
7. Delete buckets
8. Create random bucket name string
9. Create a bucket using RightAws::S3::Bucket API in a particular location 'US'
10. Create an array of 25 objects and add them to the bucket
11. Check that the bucket.keys('max_keys' ⇒ max_keys) call returns only max_keys
12. [FAIL] Number of keys returned was not equal to max_keys
13. Delete all objects in the array
14. Delete the bucket
15. Create a bucket using RightAws::S3::Bucket API in a particular location 'US'
16. Create 10 objects with key prefix 'test_object_'
17. Use marker 't' and make sure all the keys are present
18. [FAIL] Keys returned were not equal to 10
19. Use marker 'z' and make sure none of the keys are present
20. [FAIL] More than 0 keys were returned
21. [IMPROVE] Add objects with keys in the a-t range and use a as marker
22. Delete objects
23. Delete buckets
24. Create a bucket using RightAws::S3::Bucket API in a particular location 'US'
25. Add objects with keys 'mydir-help-man1' 'mydir-help-man2' 'mydir-help-man3' 'mydir-test1'
26. Check that prefix ⇒ 'mydir-' and delimiter ⇒ '-' returns 1 key
27. [FAIL] More than 1 key
28. [IMPROVE] check the keys to make sure it is the right one
29. [IMPROVE] change the delimiter to something else try again
30. Delete objects
31. Delete Bucket



# Eucalyptus Testunit Framework

Eucalyptus Testunit Framework is designed to run a list of test scripts written by Eucalyptus developers.



## How to Set Up Testunit Environment

On **Ubuntu** Linux Distribution,

### 1. UPDATE THE IMAGE

<code>
apt-get -y update
</code>

### 2. BE SURE THAT THE CLOCK IS IN SYNC

<code>
apt-get -y install ntp
</code>

<code>
date
</code>

### 3. INSTALL DEPENDENCIES
<note>
YOUR TESTUNIT **MIGHT NOT** NEED ALL THE PACKAGES BELOW; CHECK THE TESTUNIT DESCRIPTION.
</note>

<code>
apt-get -y install git-core bzr gcc make ruby libopenssl-ruby curl rubygems swig help2man libssl-dev python-dev libright-aws-ruby nfs-common openjdk-6-jdk zip libdigest-hmac-perl libio-pty-perl libnet-ssh-perl euca2ools
</code>

### 4. CLONE test_share DIRECTORY FOR TESTUNIT
<note>
YOUR TESTUNIT **MIGHT NOT** NEED test_share DIRECTORY. CHECK THE TESTUNIT DESCRIPTION.
</note>

<code>
git clone git://github.com/eucalyptus-qa/test_share.git
</code>

### 4.1. CREATE /home/test-server/test_share DIRECTORY AND LINK IT TO THE CLONED test_share

<code>
mkdir -p /home/test-server
</code>

<code>
ln -s ~/test_share/ /home/test-server/.
</code>

### 5. CLONE TESTUNIT OF YOUR CHOICE

<code>
git clone git://github.com/eucalyptus-qa/**testunit_of_your_choice**
</code>

### 6. CHANGE DIRECTORY

<code>
cd ./**testunit_of_your_choice**
</code>

### 7. CREATE 2b_tested.lst FILE in ./input DIRECTORY

<code>
vim ./input/2b_tested.lst
</code>

### 7.1. TEMPLATE OF 2b_tested.lst, SEPARATED BY TAB

<sample>
192.168.51.85	CENTOS	6.3	64	REPO	[CC00 UI CLC SC00 WS]

192.168.51.86	CENTOS	6.3	64	REPO	[NC00]
</sample>

### 7.2. BE SURE THAT YOUR MACHINE's id_rsa.pub KEY IS INCLUDED THE CLC's authorized_keys LIST

ON **YOUR TEST MACHINE**:

<code>
cat ~/.ssh/id_rsa.pub
</code>

ON **CLC MACHINE**:

<code>
vim ~/.ssh/authorized_keys
</code>

### 8. RUN THE TEST

<code>
./run_test.pl **testunit_of_your_choice.conf**
</code>


## How to Examine the Test Result

### 1. GO TO THE artifacts DIRECTORY

<code>
cd ./artifacts
</code>

### 2. CHECK OUT THE RESULT FILES

<code>
ls -l
</code>


## How to Rerun the Testunit

### 1. CLEAN UP THE ARTIFACTS

<code>
./cleanup_test.pl
</code>

### 2. RERUN THE TEST

<code>
./run_test.pl **testunit_of_your_choice.conf**
</code>


