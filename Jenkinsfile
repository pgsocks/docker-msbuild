#!/usr/bin/env groovy

pipeline {

	agent {
		label "Windows && Docker"
	}

	parameters {
		string (
				name: "VS_VERSION",
				defaultValue: "16",
				description: "What version of VS to install?" )
		string (
				name: "WORKLOAD",
				defaultValue: "VCTools",
				description: "What VS workloads to install?" )
		string (
				name: "WIN_VERSION",
				defaultValue: "1809",
				description: "What nanoserver image tag to base from?" )
	}

	stages {
		stage("Building image") {
			steps {
			  bat '''
			      docker build ^
				  --build-arg WIN_VERSION=%WIN_VERSION% ^
				  --build-arg VS_VERSION=%VS_VERSION% ^
				  --build-arg WORKLOAD=%WORKLOAD% ^
				  -m 2GB ^
				  -t pgsocks/buildtools:%VS_VERSION%-%WORKLOAD% ^
				  docker
			  '''
			}
		}
	}

}
