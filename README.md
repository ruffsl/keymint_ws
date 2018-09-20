# keymint_ws
scratch workspace for keymint testing

> save this file in ~/example:
##### talker_listener.xml

``` xml
<?xml version="1.0" encoding="UTF-8"?>

<profiles xmlns:xi="http://www.w3.org/2001/XInclude">
    <profile name="My Talker Profile">
        <attachments>
            <attachment>/*/talker</attachment>
        </attachments>
        <xi:include href="common/node.xml" parse="xml" />

        <ros_topic qualifier="ALLOW">
            <attachments>
                <attachment>{namespace}/chatter</attachment>
            </attachments>
            <permissions>
                <ros_publish/>
            </permissions>
        </ros_topic>
    </profile>

    <profile name="My Listener Profile">
        <attachments>
            <attachment>/*/listener</attachment>
        </attachments>
        <xi:include href="common/node.xml" parse="xml" />

        <ros_topic qualifier="ALLOW">
            <attachments>
                <attachment>{namespace}/chatter</attachment>
            </attachments>
            <permissions>
                <ros_subscribe/>
            </permissions>
        </ros_topic>
    </profile>
</profiles>
```

> run these commands from the same pwd:

``` shell
cd ~/example
docker run -it --rm -v=`pwd`:/root/keymint_ws keymint/keymint_tools:latest
keymint keystore init --bootstrap=keymint_ros
cp talker_listener.xml profile/comarmor.d/
keymint keystore create_pkg foo/bar/talker
keymint keystore create_pkg foo/bar/listener
keymint keystore build_pkg src/foo/bar/talker
keymint keystore build_pkg src/foo/bar/listener
exit
```

> Now try the following with and without `__ns:` set:

``` shell
export ROS_SECURITY_ROOT_DIRECTORY=`pwd`/install
export ROS_SECURITY_ENABLE=true
export ROS_SECURITY_STRATEGY=Enforce

ros2 run demo_nodes_cpp talker __ns:=/foo/bar
ros2 run demo_nodes_cpp listener __ns:=/foo/bar
```
