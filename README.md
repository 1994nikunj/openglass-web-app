<img src="client/public/favicon.png" align="right" height=100/>

# OpenGlass: Showcase yourself through your work

> OpenGlass is a web app with the primary goal of serving as an application showcase platform where developers can exhibit their work and receive feedback from others via comments, likes, and contribution prospects.

## FEATURE LIST OVERVIEW

- [x] 1. Main Page: Search/Filter projects based on technologies.
- [x] 2. Post Project: Authenticated users can add projects as per the defined schema.
- [x] 3. My projects: Allows users to retrieve their project(s).
- [x] 4. Individual project page: Displays details for the selected project and show relevant outline of information.
- [x] 5. User Profile page: Displays the user’s project and other details.
- [x] 6. Saved projects: Displays all the project(s) saved/bookmarked by the user.
- [x] 7. Portfolio: Turn the Profile-Page into a portfolio website
- [x] 8. Idea section: Post project ideas and allow contributors.
- [x] 9. Edit/Delete project: Authenticated users can modify/delete their project(s).
- [x] 10. Interaction: Authenticated users can Like, Comment on any project or Save/Bookmark them
- [x] 11. Hiring Section: Shows all the users available for hire and can be filtered based on skills and availability
- [x] 12. Upload media to S3 and store its endpoint in the database

## TECHNOLOGY STACK

THis application is built using [`MERN`](https://www.mongodb.com/mern-stack) stacks
<img src="https://user-images.githubusercontent.com/51209322/208287963-5735fb30-281d-4b93-8c20-bfca6f1403d6.png" align="right" height=150/>

- [`MongoDB`](https://www.mongodb.com/) - DATABASE
- [`Express`](https://www.mongodb.com/) - SERVER
- [`React`](https://www.mongodb.com/) - WEB
- [`Node`](https://www.mongodb.com/) - SERVER

## DATABASE SCHEMA IN USE

> Users Collection

```json
{
	"_id": "638a922d97cd9732b83106a8",
	"firstName": "Nikunj",
	"lastName": "Sharma",
	"username": "nik",
	"dob": "03-05-1970",
	"bio": null,
	"email": "nik@gmail.com",
	"password": "somebcrpytstring",
	"education": [
		{
			"_id": "7b7997a2-c0d2-4f8c-b27a-6a1d4b5b620",
			"school": "Stevens Institute of Technology",
			"course": "MS in Computer Science",
			"from": "08-12-2018",
			"to": "08-24-2020"
		}
	],
	"skills": ["react"],
	"experience": [
		{
			"_id": "7b7997a2-c0d2-4f8c-b27a-6a1d4b5b610",
			"company": "Google",
			"position": "Software Developer Engineer",
			"from": "09-12-2020",
			"to": "10-19-2021"
		}
	],
	"socials": {
		"github": "https://github.com/199nik/test",
		"linkedin": null
	}
}
```

> Projects Collection

```json
{
	"_id": "639181477a14df2ee3ee937a",
	"name": "Aftersell Casestudy 3D illustration",
	"description": "Description here",
	"github": "https://github.com/199nik/test",
	"media": [],
	"deploymentLink": "https://www.github.com",
	"createdAt": "2022-12-08T06:16:39.174Z",
	"updatedAt": "2022-12-08T06:16:39.174Z",
	"technologies": ["python", "django"],
	"owner": {
		"_id": "638a922d97cd9732b83106a8",
		"username": "nik"
	},
	"savedBy": ["638a922d97cd9732b83106a8", "639182577a14df2ee3ee937c"],
	"comments": [
		{
			"_id": "639182237a14df2ee3ee937b",
			"comment": "Nice! This is awesome",
			"createdAt": "2022-12-08T06:20:19.508Z",
			"owner": {
				"_id": "638a922d97cd9732b83106a8",
				"username": "nik"
			}
		}
	],
	"likes": ["639183fc7a14df2ee3ee937ft", "1245e83fc7a14df2ee1d2xcvt"]
}
```

> Ideas Collection

```json
{
	"_id": "638aaab41cdca2fb05c054f5",
	"name": "CV Generator -NEW",
	"description": "Responsive Portfolio Website",
	"status": "active",
	"lookingFor": 2,
	"createdAt": "2022-12-03T01:47:32.083Z",
	"technologies": ["html", "react"],
	"owner": {
		"_id": "638a922d97cd9732b83106a8",
		"username": "nik"
	},
	"comments": [
		{
			"_id": "639182237a14df2ee3ee937b",
			"comment": "Nice! This is awesome",
			"createdAt": "2022-12-08T06:20:19.508Z",
			"owner": {
				"_id": "638a922d97cd9732b83106a8",
				"username": "nik"
			}
		}
	],
	"likes": ["639183fc7a14df2ee3ee937ft", "1245e83fc7a14df2ee1d2xcvt"],
	"updatedAt": "2022-12-03T03:09:37.879Z"
}
```

> Note: The allowed ranges and types for the input fields have been put in a separate file (collections__type-and-range.pdf) which is in the parent directory in the zip.
- - - -
# Setup

## Step I. Clone URL (optional)

> https://github.com/1994nikunj/openglass-web-app

## Step II. Installing dependencies

Install npm dependencies in both the `client` and `server` sub-directories and also the root directory.

```shell
> npm install
# go to the 'server' directory and execute the below
> cd server && npm install
# go to the 'client' directory and execute the below
> cd client && npm install
```

The root directory has been initialized as an npm project and installs [`concurrently`](https://www.npmjs.com/package/concurrently) as a dev dependency to start both the client and the server with a single command

Set up a MongoDB database either locally or online via <a href='https://www.mongodb.com/cloud/atlas'>MongoDB Atlas</a>

Create a `.env` file in both the `client` and `server` subdirectories as shown in the `.env.example` files

## Step III: Setting up environment variables:
> Note: the zipped file will already contain the .env files with the below entries  

```ini
In `client/.env`:
REACT_APP_SERVER_URL="http://localhost:3005" //endpoint on which server will start

In `server/.env`:
MONGO_URL= //MongoDB database endpoint
MONGO_DATABASE= //name of the database
JWT_SECRET= //string used for JWT secret
AWS_S3_BUCKET_NAME= //S3 bucket name
AWS_S3_SECRET_ACCESS_KEY= //S3 bucket access key
AWS_S3_ACCESS_KEY_ID= //S3 bucked access key id
AWS_S3_REGION= //S3 region
ENVIRONMENT="local" //environment currently working on - used for storing media according to environment
```

## Step IV: Running the application

To run the code, from the root directory you can start the application in development mode using:
```shell
$ npm start
```
