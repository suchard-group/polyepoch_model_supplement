# Inhomogeneous continuous-time Markov chains to infer flexible time-varying evolutionary rates

This repository contains the instructions and files to reproduce the analyses performed 
in the "Inhomogeneous continuous-time Markov chains to infer flexible time-varying 
evolutionary rates" paper by Datta et al. 

### Setting up BEAGLE
Please follow the [BEAGLE installation instructions](https://github.com/beagle-dev/beagle-lib).
But get the `hmc-clock` branch.

For Mac users, the following commands will compile the CPU version of BEAGLE.
Follow the [instructions](https://github.com/beagle-dev/beagle-lib) if you need to install any other dependent software.

```
xcode-select --install
brew install libtool autoconf automake
git clone -b hmc-clock https://github.com/beagle-dev/beagle-lib.git
cd beagle-lib
./autogen.sh
./configure --without-opencl --without-cuda
sudo make install
```


For Linux users, the commands are similar.

```
sudo apt-get install build-essential autoconf automake libtool git pkg-config openjdk-9-jdk
git clone -b hmc-clock https://github.com/beagle-dev/beagle-lib.git
cd beagle-lib
./autogen.sh
./configure --without-opencl --without-cuda
sudo make install
```


The libraries are installed into `/usr/local/lib`.
You can find them by `ls /usr/local/lib/*beagle*`.


### Setting up BEAST

The following commands will compile the `hmc-clock` branch of BEAST.

```
git clone -b hmc-clock https://github.com/beast-dev/beast-mcmc.git
cd beast-mcmc
ant
```

For Mac users, you may need to install ant by `brew install ant` through [Homebrew](https://brew.sh/).

For Linux users, you can install ant by `sudo apt-get install ant`.

This will compile the `jar` files under `beast-mcmc/build/dist/` where you can find `beast.jar`, `beauti.jar` and `trace.jar`.

### Reproducing the analyses

You may use the following commands to run the analyses described in the manuscript.

Change your working directory to where you want to store the resulting log files first.

```
cd where_you_want_to_save_results
```

#### Strict Clock Rate Simulation

* Simulate sequences under strict clock
	

	```
	java -jar -Djava.library.path=/usr/local/lib where_beast_is_git_cloned/beast-mcmc/build/dist/beast.jar -seed 6662 -overwrite where_this_repository_is_stored/xml/Simulation_Study/Constant_Rate/Constant_Rate_Simulation.xml
	```
	
	
	

* Fit true model


	```
	java -jar -Djava.library.path=/usr/local/lib where_beast_is_git_cloned/beast-mcmc/build/dist/beast.jar -seed 6662 -overwrite where_this_repository_is_stored/xml/Simulation_Study/Constant_Rate/Constant_Rate_True_Model.xml
	```
	
* Fit polyepoch clock model

	```
	java -jar -Djava.library.path=/usr/local/lib where_beast_is_git_cloned/beast-mcmc/build/dist/beast.jar -seed 6662 -overwrite where_this_repository_is_stored/xml/Simulation_Study/Constant_Rate/Constant_Rate_Polyepoch_Clock.xml
	```	
	

#### Log Linear Rate Simulation

* Simulate sequences under log linear rate
	

	```
	java -jar -Djava.library.path=/usr/local/lib where_beast_is_git_cloned/beast-mcmc/build/dist/beast.jar -seed 6662 -overwrite where_this_repository_is_stored/xml/Simulation_Study/Log_Linear_Rate/Log_Linear_Rate_Simulation.xml
	```
	

* Fit true model


	```
	java -jar -Djava.library.path=/usr/local/lib where_beast_is_git_cloned/beast-mcmc/build/dist/beast.jar -seed 6662 -overwrite where_this_repository_is_stored/xml/Simulation_Study/Log_Linear_Rate/Log_Linear_Rate_True_Model.xml
	```
	
* Fit polyepoch clock model

	```
	java -jar -Djava.library.path=/usr/local/lib where_beast_is_git_cloned/beast-mcmc/build/dist/beast.jar -seed 6662 -overwrite where_this_repository_is_stored//Users/pratyusa/xml/Simulation_Study/Log_Linear_Rate/Log_Linear_Rate_Polyepoch_Clock.xml
	```	
	



#### West Nile Virus


* Fit polyepoch clock model
	

	```
	java -jar -Djava.library.path=/usr/local/lib where_beast_is_git_cloned/beast-mcmc/build/dist/beast.jar -seed 6662 -overwrite where_this_repository_is_stored/xml/West_Nile_Virus/wnv_pcm.xml
	```
	

* Fit strict clock model


	```
	java -jar -Djava.library.path=/usr/local/lib where_beast_is_git_cloned/beast-mcmc/build/dist/beast.jar -seed 6662 -overwrite where_this_repository_is_stored/xml/West_Nile_Virus/wnv_scr.xml
	```
	
* Marginal likelihood estimation under polyepoch clock model

	```
	java -jar -Djava.library.path=/usr/local/lib where_beast_is_git_cloned/beast-mcmc/build/dist/beast.jar -seed 6662 -overwrite where_this_repository_is_stored//Users/pratyusa/xml/West_Nile_Virus/wnv_pcm_mar_lik.xml
	```	


* Marginal likelihood estimation under strict clock model

	```
	java -jar -Djava.library.path=/usr/local/lib where_beast_is_git_cloned/beast-mcmc/build/dist/beast.jar -seed 6662 -overwrite where_this_repository_is_stored//Users/pratyusa//Users/pratyusa/xml/West_Nile_Virus/wnv_scr_mar_lik.xml
	```	
	


#### Dengue Virus


* Fit polyepoch clock model


	```
	java -jar -Djava.library.path=/usr/local/lib where_beast_is_git_cloned/beast-mcmc/build/dist/beast.jar -seed 6662 -overwrite where_this_repository_is_stored/xml/Dengue/dengue_pcm.xml
	```
	
* Marginal likelihood estimation under polyepoch clock model

	```
	java -jar -Djava.library.path=/usr/local/lib where_beast_is_git_cloned/beast-mcmc/build/dist/beast.jar -seed 6662 -overwrite where_this_repository_is_stored/xml/Dengue/dnv_pcm_mar_lik.xml
	```

* Marginal likelihood estimation under random local clock model

	```
	java -jar -Djava.library.path=/usr/local/lib where_beast_is_git_cloned/beast-mcmc/build/dist/beast.jar -seed 6662 -overwrite where_this_repository_is_stored/xml/Dengue/dengue_rlc_mar_lik.xml
	```
	
#### Seasonal Influenza A/H3N2

* Fit polyepoch clock model


	```
	java -jar -Djava.library.path=/usr/local/lib where_beast_is_git_cloned/beast-mcmc/build/dist/beast.jar -seed 6662 -overwrite where_this_repository_is_stored/xml/Flu/flu.xml
	```
	
#### SARS-CoV-2

* Fit polyepoch clock model


	```
	java -jar -Djava.library.path=/usr/local/lib where_beast_is_git_cloned/beast-mcmc/build/dist/beast.jar -seed 6662 -overwrite where_this_repository_is_stored/xml/SARS_CoV_2/sc2.xml
	```
	
#### Lassa

* Fit polyepoch clock model


	```
	java -jar -Djava.library.path=/usr/local/lib where_beast_is_git_cloned/beast-mcmc/build/dist/beast.jar -seed 6662 -overwrite where_this_repository_is_stored/xml/Lassa/lassa.xml
	```

