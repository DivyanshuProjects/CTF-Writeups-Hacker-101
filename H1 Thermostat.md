Hi! I'm Divyanshu, and I’m passionate about cybersecurity, reverse engineering, and exploring the internals of mobile apps. In this blog, I’ll walk you through my approach to solving the H1 Thermostat Android CTF, where we had to reverse an APK to uncover a hidden flag. Whether you're just getting into CTFs or have some experience, this writeup is for you

🧩 Challenge Overview
CTF Name: H1 Thermostat
Platform: Android
Goal: Find the flag hidden within the APK file.

We were provided a single file: thermostat.apk. Our mission? Crack it open and uncover the flag hidden somewhere inside.

⚙️ Environment Setup
I used Kali Linux for this challenge, but you can follow along using any Linux distro or even Windows/macOS with the right tools.

🧰 Tools I Used:
unzip — to extract the APK contents

jadx-gui — to reverse engineer the APK and read its Java source code

A sharp eye for patterns, search keywords, and some manual exploration

You could also use Android Studio, apktool, or MobSF, but I prefer jadx-gui for quick and clean Java code browsing.

🕵️ Step-by-Step Walkthrough
🔓 Step 1: Unzipping the APK
An APK file is essentially a ZIP archive. I started by extracting its contents:

bash
Copy
Edit
unzip thermostat.apk -d thermostat_extracted
This gave me access to a variety of files:

classes.dex — the compiled Dalvik bytecode

AndroidManifest.xml

Resources and assets folders

🧠 Step 2: Opening the Code with JADX
To read through the bytecode in a human-readable format, I used jadx-gui, a powerful decompiler for Android apps:

bash
Copy
Edit
jadx-gui thermostat.apk
Once open, JADX showed me the full directory structure and decompiled Java code.

🔍 Step 3: Exploring the Java Files
From experience, CTF flags are often hidden in either:

Hardcoded values

Specific functions related to authentication or payloads

Custom packages like com.hacker101 (a common namespace in HackerOne CTFs)

So I navigated directly to:

Copy
Edit
com.hacker101.app
There, I found a file called PayloadRequest.java.

This file stood out. Upon inspection, I found what looked like a hardcoded flag.

🎯 Step 4: Finding the Flag
Inside PayloadRequest.java, I saw something like this (edited to avoid spoilers):

java
Copy
Edit
public class PayloadRequest {
    public static final String FLAG = "flag{***********}";
}
Bingo! That was our flag.

![Screenshot 2025-04-16 235215](https://github.com/user-attachments/assets/8d4d2490-c034-43d2-97f0-cdb20b57e5f8)


💡 What You Can Learn from This CTF
APK files are not secure by default — reverse engineering is fairly straightforward with the right tools.

Static analysis using tools like JADX is often enough to find the flag, especially in beginner/intermediate-level challenges.

Look for suspicious or standout package names like com.hacker101.

Think like a developer — if you had to hardcode something, where would you hide it?

🧰 Alternative Tools to Try
Here are a few other tools you might want to experiment with for deeper analysis:

apktool – great for decoding resources and manifest files.

MobSF (Mobile Security Framework) – an all-in-one automated analysis tool.

Frida or Xposed – for runtime dynamic analysis if static doesn't cut it.

📝 Final Thoughts
This was a fun and educational challenge that tested basic Android reverse engineering skills. If you're new to mobile CTFs, this is a great starting point. And remember — always think like both an attacker and a developer.

Stay curious, stay persistent, and happy hacking!
— Divyanshu
