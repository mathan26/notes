## Mapstruct and Lombok

 - Annotation processor used for generate code by specifying the annotations.
 - Mapstuct used for converting DTO to Domain and vice versa.
 - Lombok used for in the POJO classes mostly for getter, setter, constrcotr , equals and hashcode auto creations
 - dependencies need to be added:
	 
		 `<dependency>
			<groupId>org.mapstruct</groupId>
			<artifactId>mapstruct</artifactId>
			<version>${mapstruct.version}</version></dependency>`
    
	         <plugin>
	    			<groupId>org.apache.maven.plugins</groupId>
	    				<artifactId>maven-compiler-plugin</artifactId>
	    				<version>3.8.0</version>
	    				<configuration>
	    					<annotationProcessorPaths>
	    						<path>
	    							<groupId>org.mapstruct</groupId>
	    							<artifactId>mapstruct-processor</artifactId>
	    							<version>${mapstruct.version}</version>
	    						</path>
	    						<path>
	    							<groupId>org.projectlombok</groupId>
	    							<artifactId>lombok</artifactId>
	    							<version>${org.lombok.version}</version>
	    						</path>
	    						<path>
	    							<groupId>org.projectlombok</groupId>
	    							<artifactId>lombok-mapstruct-binding</artifactId>
	    							<version>0.2.0</version>
	    						</path>
	    					</annotationProcessorPaths>
	    					<compilerArgs>
	    						<compilerArg>-Amapstruct.defaultComponentModel=spring</compilerArg>
	    					</compilerArgs>
	    				</configuration>
	    			</plugin>
	
 - Above plugins is need for for mapstruct to work along with lombok.

**Mapstuct uses in conversion**

 - When DTO and domain have different data type that time we can create separate class that has both conversion we can inject this into the mapper inteface as below generate auto conversion,
 

	    @Mapper(uses = {DateMapper.class})

**84. Added circle ci**

 - login to circleci.com give access to the git repository.
 - copy the yml file create .circleci folder in the project put the config.yml set the java--11 
 - commit it circle ci will build for you if any test fail it build will be failed.
 - copy the badge from setting paste it in the readme it will show the result as pass or failed.
