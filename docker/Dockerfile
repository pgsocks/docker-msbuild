# escape=`

ARG WIN_VERSION="1809"
FROM mcr.microsoft.com/windows/servercore:$WIN_VERSION AS install

SHELL [ "cmd", "/S", "/C" ]

ARG VS_VERSION="16"
ARG VS_SRC="https://aka.ms/vs/${VS_VERSION}/release/vs_buildtools.exe"
ARG WORKLOAD

RUN curl -SL --output vs_buildtools.exe %VS_SRC%
RUN start /w vs_buildtools.exe --quiet --wait --norestart `
--addProductLang en-US `
--add Microsoft.VisualStudio.Workload.%WORKLOAD% `
--includeRecommended

LABEL msbuild.version="${VS_VERSION}"
LABEL msbuild.workload="${WORKLOAD}"
