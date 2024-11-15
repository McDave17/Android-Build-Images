FROM openjdk:17-jdk-bullseye
LABEL maintainer=mcdermottdavid396@gmail.com
CMD ["bash"]
RUN apt-get -q update -y && apt-get -q upgrade -y
RUN apt-get -q update -y && apt-get -q install -y wget tar unzip libstdc++6 libz1
ENV ANDROID_HOME=/android-home
ENV ANDROID_COMPILE_SDK=35
ENV ANDROID_BUILD_TOOLS=35.0.0
ENV ANDROID_SDK_TOOLS=11076708
RUN install -d $ANDROID_HOME
RUN wget -nv -O $ANDROID_HOME/cmdline-tools.zip https://dl.google.com/android/repository/commandlinetools-linux-${ANDROID_SDK_TOOLS}_latest.zip
RUN cd $ANDROID_HOME && unzip cmdline-tools.zip && cd ..
ENV PATH=/usr/local/openjdk-17/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/android-home/cmdline-tools/bin/
RUN sdkmanager --sdk_root=${ANDROID_HOME} --version
RUN yes | sdkmanager --sdk_root=${ANDROID_HOME} --licenses || true
RUN sdkmanager --sdk_root=${ANDROID_HOME} "platforms;android-${ANDROID_COMPILE_SDK}"
RUN sdkmanager --sdk_root=${ANDROID_HOME} "platform-tools"
RUN sdkmanager --sdk_root=${ANDROID_HOME} "build-tools;${ANDROID_BUILD_TOOLS}"
CMD ["jshell"]
