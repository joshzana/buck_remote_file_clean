##This sample illustrates some bad interaction between buck cache, buck clean, and remote_file rules.  To repro:

	buck clean 
Shutting down nailgun server...
Using watchman.
Using buckd.

	buck build app

	echo "" >> java/com/example/activity/MyFirstActivity.java 

	buck build app

/Users/joshzana/src/buck_remote_file_clean/java/com/example/activity/MyFirstActivity.java:6: error: package javax.annotation does not exist
import javax.annotation.Nonnull;
                       ^
/Users/joshzana/src/buck_remote_file_clean/java/com/example/activity/MyFirstActivity.java:11: error: cannot find symbol
  public void onCreate(@Nonnull Bundle savedInstanceState) {
                        ^
  symbol:   class Nonnull
  location: class com.example.activity.MyFirstActivity
Errors: 2. Warnings: 0.
BUILD FAILED: //java/com/example/activity:activity failed with exit code 1:
javac
