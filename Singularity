BootStrap: docker
From: ubuntu:bionic


%labels
    MAINTAINER verysure

%post
    dpkg --add-architecture i386
    apt-get -qq update --fix-missing 
    apt-get install -yq wget curl software-properties-common adb git 
    apt-get install -yq qemu libpulse0 libglu1-mesa xvfb libxcomposite-dev
    apt-get install -yq libc6:i386 libncurses5:i386 libstdc++6:i386 lib32z1 libbz2-1.0:i386 x11-apps

    # install nodejs
    curl -sL https://deb.nodesource.com/setup_13.x | bash -
    apt-get install -y nodejs

    # java
    wget -qO - https://adoptopenjdk.jfrog.io/adoptopenjdk/api/gpg/key/public | apt-key add -
    add-apt-repository --yes https://adoptopenjdk.jfrog.io/adoptopenjdk/deb/
    apt-get install -y software-properties-common
    add-apt-repository --yes https://adoptopenjdk.jfrog.io/adoptopenjdk/deb/
    apt-get update
    apt-get -y install adoptopenjdk-8-hotspot

    # yarn
    curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | apt-key add -
    echo "deb https://dl.yarnpkg.com/debian/ stable main" | tee /etc/apt/sources.list.d/yarn.list
    apt-get update
    apt-get -y install yarn

    # android-studio
    wget https://dl.google.com/dl/android/studio/ide-zips/3.6.3.0/android-studio-ide-192.6392135-linux.tar.gz -O /opt/android-studio.tar.gz
    cd /opt
    tar xzvf android-studio.tar.gz
    rm android-studio.tar.gz

    # end
    apt-get clean -yq

%environment
export ANDROID_SDK_ROOT=$HOME/Android/Sdk
export PATH=$PATH:/opt/android-studio/bin
export PATH=$PATH:$ANDROID_SDK_ROOT/emulator
export PATH=$PATH:$ANDROID_SDK_ROOT/tools
export PATH=$PATH:$ANDROID_SDK_ROOT/tools/bin
export PATH=$PATH:$ANDROID_SDK_ROOT/platform-tools




