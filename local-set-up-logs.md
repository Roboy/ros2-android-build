- `python3 run.py ../ros2-android-test-app/app/src/main/jniLibs ../ros2-android-test-app/app/libs --srcDir ../ros2-android-test-app/app/src`
> Failed   <<< fastcdr [0.88s, exited with code 1]
Aborted  <<< ament_flake8 [0.63s]
Aborted  <<< ament_cmake_core [1.15s]
Aborted  <<< gmock_vendor [1.74s]

Summary: 4 packages finished [9.73s]
  1 package failed: fastcdr
  3 packages aborted: ament_cmake_core ament_flake8 gmock_vendor
  3 packages had stderr output: ament_cmake_core fastcdr gmock_vendor
  144 packages not processed
Traceback (most recent call last):
  File "run.py", line 112, in <module>
    main()
  File "run.py", line 108, in main
    output(workspacePath, soOutPath, jarOutPath)
  File "run.py", line 76, in output
    shutil.copyfile(filepath, distFilePath)
  File "/Users/eminvergili/opt/anaconda3/lib/python3.8/shutil.py", line 264, in copyfile
    with open(src, 'rb') as fsrc, open(dst, 'wb') as fdst:
FileNotFoundError: [Errno 2] No such file or directory: '/Users/eminvergili/Projects/Roboy/ros2-android-docker-build/ros2-android-build/tmp/libc++_shared.so'

> Solution: https://stackoverflow.com/a/71611002

- Change android abi at dockerfile to x86_64 according to https://developer.android.com/ndk/guides/abis and http://developer.segwayrobotics.com/developer/documents/segway-robot-overview.html

- Change time zone accordingly

- Stuck a few hours at colcon build step:
```
/usr/bin/qemu-x86_64 

/usr/bin/javac /usr/bin/javac 

-classpath :/home/user/workspace/build/shape_msgs/shape_msgs__java
            :/home/user/workspace/build/shape_msgs/shape_msgs__java
            :/home/user/workspace/install/rcljava_common/share/rcljava_common/java/commons-lang3-3.7.jar
            :/home/user/workspace/install/rcljava_common/share/rcljava_common/java/slf4j-api-1.7.21.jar
            :/home/user/workspace/install/rcljava_common/share/rcljava_common/java/slf4j-android-1.7.21.jar
            :/home/user/workspace/install/rcljava_common/share/rcljava_common/java/rcljava_common.jar
            :/home/user/workspace/install/geometry_msgs/share/geometry_msgs/java/geometry_msgs_messages.jar
            :/home/user/workspace/install/std_msgs/share/std_msgs/java/std_msgs_messages.jar
            :/home/user/workspace/install/builtin_interfaces/share/builtin_interfaces/java/builtin_interfaces_messages.jar
            
-d /home/user/workspace/build/shape_msgs/shape_msgs__java/CMakeFiles/shape_msgs_messages_jar.dir 

@/home/user/workspace/build/shape_msgs/shape_msgs__java/CMakeFiles/shape_msgs_messages_jar.dir/java_sources
```
> Stop and rerun python command

<!-- - On python command
> WARNING: The requested image's platform (linux/amd64) does not match the detected host platform (linux/arm64/v8) and no specific platform was requested
> Add `--platform linux/amd64` to docker commands at `run.py` and `arch -x86_64 zsh` -->

- On python command
```
=== /home/user/workspace/src/ament/ament_cmake (git) ===
Could not create directory '/home/user/workspace/src/ament/ament_cmake': [Errno 1] Operation not permitted: '/home/user/workspace/src/ament'
=== /home/user/workspace/src/ament/ament_index (git) ===
Could not create directory '/home/user/workspace/src/ament/ament_index': [Errno 1] Operation not permitted: '/home/user/workspace/src/ament'
=== /home/user/workspace/src/ament/ament_lint (git) ===
Could not create directory '/home/user/workspace/src/ament/ament_lint': [Errno 1] Operation not permitted: '/home/user/workspace/src/ament'
=== /home/user/workspace/src/ament/ament_package (git) ===
Could not create directory '/home/user/workspace/src/ament/ament_package': [Errno 1] Operation not permitted: '/home/user/workspace/src/ament'
=== /home/user/workspace/src/ament/google_benchmark_vendor (git) ===
Could not create directory '/home/user/workspace/src/ament/google_benchmark_vendor': [Errno 1] Operation not permitted: '/home/user/workspace/src/ament'
=== /home/user/workspace/src/ament/googletest (git) ===
Could not create directory '/home/user/workspace/src/ament/googletest': [Errno 1] Operation not permitted: '/home/user/workspace/src/ament'
=== /home/user/workspace/src/ament/uncrustify_vendor (git) ===
Could not create directory '/home/user/workspace/src/ament/uncrustify_vendor': [Errno 1] Operation not permitted: '/home/user/workspace/src/ament'
=== /home/user/workspace/src/eProsima/Fast-CDR (git) ===
Could not create directory '/home/user/workspace/src/eProsima/Fast-CDR': [Errno 1] Operation not permitted: '/home/user/workspace/src/eProsima'
=== /home/user/workspace/src/eProsima/Fast-DDS (git) ===
Could not create directory '/home/user/workspace/src/eProsima/Fast-DDS': [Errno 1] Operation not permitted: '/home/user/workspace/src/eProsima'
=== /home/user/workspace/src/eProsima/foonathan_memory_vendor (git) ===
Could not create directory '/home/user/workspace/src/eProsima/foonathan_memory_vendor': [Errno 1] Operation not permitted: '/home/user/workspace/src/eProsima'
=== /home/user/workspace/src/osrf/osrf_pycommon (git) ===
Could not create directory '/home/user/workspace/src/osrf/osrf_pycommon': [Errno 1] Operation not permitted: '/home/user/workspace/src/osrf'
=== /home/user/workspace/src/osrf/osrf_testing_tools_cpp (git) ===
Could not create directory '/home/user/workspace/src/osrf/osrf_testing_tools_cpp': [Errno 1] Operation not permitted: '/home/user/workspace/src/osrf'
=== /home/user/workspace/src/ros-tooling/libstatistics_collector (git) ===
Could not create directory '/home/user/workspace/src/ros-tooling/libstatistics_collector': [Errno 1] Operation not permitted: '/home/user/workspace/src/ros-tooling'
=== /home/user/workspace/src/ros-tracing/ros2_tracing (git) ===
Could not create directory '/home/user/workspace/src/ros-tracing/ros2_tracing': [Errno 1] Operation not permitted: '/home/user/workspace/src/ros-tracing'
=== /home/user/workspace/src/ros2-java/ament_java (git) ===
Could not create directory '/home/user/workspace/src/ros2-java/ament_java': [Errno 1] Operation not permitted: '/home/user/workspace/src/ros2-java'
=== /home/user/workspace/src/ros2-java/ros2_android (git) ===
Could not create directory '/home/user/workspace/src/ros2-java/ros2_android': [Errno 1] Operation not permitted: '/home/user/workspace/src/ros2-java'
=== /home/user/workspace/src/ros2-java/ros2_android_examples (git) ===
Could not create directory '/home/user/workspace/src/ros2-java/ros2_android_examples': [Errno 1] Operation not permitted: '/home/user/workspace/src/ros2-java'
=== /home/user/workspace/src/ros2-java/ros2_java (git) ===
Could not create directory '/home/user/workspace/src/ros2-java/ros2_java': [Errno 1] Operation not permitted: '/home/user/workspace/src/ros2-java'
=== /home/user/workspace/src/ros2/ament_cmake_ros (git) ===
Could not create directory '/home/user/workspace/src/ros2/ament_cmake_ros': [Errno 1] Operation not permitted: '/home/user/workspace/src/ros2'
=== /home/user/workspace/src/ros2/common_interfaces (git) ===
Could not create directory '/home/user/workspace/src/ros2/common_interfaces': [Errno 1] Operation not permitted: '/home/user/workspace/src/ros2'
=== /home/user/workspace/src/ros2/example_interfaces (git) ===
Could not create directory '/home/user/workspace/src/ros2/example_interfaces': [Errno 1] Operation not permitted: '/home/user/workspace/src/ros2'
=== /home/user/workspace/src/ros2/launch (git) ===
Could not create directory '/home/user/workspace/src/ros2/launch': [Errno 1] Operation not permitted: '/home/user/workspace/src/ros2'
=== /home/user/workspace/src/ros2/libyaml_vendor (git) ===
Could not create directory '/home/user/workspace/src/ros2/libyaml_vendor': [Errno 1] Operation not permitted: '/home/user/workspace/src/ros2'
=== /home/user/workspace/src/ros2/performance_test_fixture (git) ===
Could not create directory '/home/user/workspace/src/ros2/performance_test_fixture': [Errno 1] Operation not permitted: '/home/user/workspace/src/ros2'
=== /home/user/workspace/src/ros2/python_cmake_module (git) ===
Could not create directory '/home/user/workspace/src/ros2/python_cmake_module': [Errno 1] Operation not permitted: '/home/user/workspace/src/ros2'
=== /home/user/workspace/src/ros2/rcl (git) ===
Could not create directory '/home/user/workspace/src/ros2/rcl': [Errno 1] Operation not permitted: '/home/user/workspace/src/ros2'
=== /home/user/workspace/src/ros2/rcl_interfaces (git) ===
Could not create directory '/home/user/workspace/src/ros2/rcl_interfaces': [Errno 1] Operation not permitted: '/home/user/workspace/src/ros2'
=== /home/user/workspace/src/ros2/rcl_logging (git) ===
Could not create directory '/home/user/workspace/src/ros2/rcl_logging': [Errno 1] Operation not permitted: '/home/user/workspace/src/ros2'
=== /home/user/workspace/src/ros2/rcpputils (git) ===
Could not create directory '/home/user/workspace/src/ros2/rcpputils': [Errno 1] Operation not permitted: '/home/user/workspace/src/ros2'
=== /home/user/workspace/src/ros2/rcutils (git) ===
Could not create directory '/home/user/workspace/src/ros2/rcutils': [Errno 1] Operation not permitted: '/home/user/workspace/src/ros2'
=== /home/user/workspace/src/ros2/rmw (git) ===
Could not create directory '/home/user/workspace/src/ros2/rmw': [Errno 1] Operation not permitted: '/home/user/workspace/src/ros2'
=== /home/user/workspace/src/ros2/rmw_dds_common (git) ===
Could not create directory '/home/user/workspace/src/ros2/rmw_dds_common': [Errno 1] Operation not permitted: '/home/user/workspace/src/ros2'
=== /home/user/workspace/src/ros2/rmw_fastrtps (git) ===
Could not create directory '/home/user/workspace/src/ros2/rmw_fastrtps': [Errno 1] Operation not permitted: '/home/user/workspace/src/ros2'
=== /home/user/workspace/src/ros2/rmw_implementation (git) ===
Could not create directory '/home/user/workspace/src/ros2/rmw_implementation': [Errno 1] Operation not permitted: '/home/user/workspace/src/ros2'
=== /home/user/workspace/src/ros2/rosidl (git) ===
Could not create directory '/home/user/workspace/src/ros2/rosidl': [Errno 1] Operation not permitted: '/home/user/workspace/src/ros2'
=== /home/user/workspace/src/ros2/rosidl_dds (git) ===
Could not create directory '/home/user/workspace/src/ros2/rosidl_dds': [Errno 1] Operation not permitted: '/home/user/workspace/src/ros2'
=== /home/user/workspace/src/ros2/rosidl_defaults (git) ===
Could not create directory '/home/user/workspace/src/ros2/rosidl_defaults': [Errno 1] Operation not permitted: '/home/user/workspace/src/ros2'
=== /home/user/workspace/src/ros2/rosidl_python (git) ===
Could not create directory '/home/user/workspace/src/ros2/rosidl_python': [Errno 1] Operation not permitted: '/home/user/workspace/src/ros2'
=== /home/user/workspace/src/ros2/rosidl_typesupport (git) ===
Could not create directory '/home/user/workspace/src/ros2/rosidl_typesupport': [Errno 1] Operation not permitted: '/home/user/workspace/src/ros2'
=== /home/user/workspace/src/ros2/rosidl_typesupport_fastrtps (git) ===
Could not create directory '/home/user/workspace/src/ros2/rosidl_typesupport_fastrtps': [Errno 1] Operation not permitted: '/home/user/workspace/src/ros2'
=== /home/user/workspace/src/ros2/rpyutils (git) ===
Could not create directory '/home/user/workspace/src/ros2/rpyutils': [Errno 1] Operation not permitted: '/home/user/workspace/src/ros2'
=== /home/user/workspace/src/ros2/test_interface_files (git) ===
Could not create directory '/home/user/workspace/src/ros2/test_interface_files': [Errno 1] Operation not permitted: '/home/user/workspace/src/ros2'
=== /home/user/workspace/src/ros2/unique_identifier_msgs (git) ===
Could not create directory '/home/user/workspace/src/ros2/unique_identifier_msgs': [Errno 1] Operation not permitted: '/home/user/workspace/src/ros2'
start building packages
Traceback (most recent call last):
  File "/usr/local/bin/colcon", line 8, in <module>
    sys.exit(main())
  File "/usr/local/lib/python3.8/dist-packages/colcon_core/command.py", line 118, in main
    return _main(command_name=command_name, argv=argv)
  File "/usr/local/lib/python3.8/dist-packages/colcon_core/command.py", line 185, in _main
    create_log_path(args.verb_name)
  File "/usr/local/lib/python3.8/dist-packages/colcon_core/location.py", line 186, in create_log_path
    os.makedirs(str(path))
  File "/usr/lib/python3.8/os.py", line 213, in makedirs
    makedirs(head, exist_ok=exist_ok)
  File "/usr/lib/python3.8/os.py", line 223, in makedirs
    mkdir(name, mode)
PermissionError: [Errno 1] Operation not permitted: 'log'
Traceback (most recent call last):
  File "run.py", line 112, in <module>
    main()
  File "run.py", line 108, in main
    output(workspacePath, soOutPath, jarOutPath)
  File "run.py", line 76, in output
    shutil.copyfile(filepath, distFilePath)
  File "/Users/eminvergili/opt/anaconda3/lib/python3.8/shutil.py", line 264, in copyfile
    with open(src, 'rb') as fsrc, open(dst, 'wb') as fdst:
FileNotFoundError: [Errno 2] No such file or directory: '/Users/eminvergili/Projects/Roboy/ros2-android-docker-build/ros2-android-build/tmp/libc++_shared.so'
```
> Probably `tmp` directory is created with wrong ownership `sudo rm -rf tmp` and rerun python command without sudo.

<!-- - takes time to restart container don't `docker run --rm` -->

- add `--executor sequential` to colcon to ease up build cpu load

- At `docker build...` step if the process stuck at
```
 => [ 5/12] RUN apt install -y git vim cmake build-essential openjdk-8-jdk                                                                                                                         364.6s
 => => # Setting up ubuntu-mono (19.04-0ubuntu3) ...
 => => # Processing triggers for libc-bin (2.31-0ubuntu9.9) ...
 => => # Processing triggers for ca-certificates (20210119~20.04.2) ...
 => => # Updating certificates in /etc/ssl/certs...
 => => # 0 added, 0 removed; done.
 => => # Running hooks in /etc/ca-certificates/update.d...
```
run with rosetta using
> `arch -x86_64 zsh` or whichever shell you are using
and then retry