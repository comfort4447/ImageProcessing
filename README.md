## Overview
This is an API that can be used in two different ways. The first, as a simple placeholder API that allows us to place images into our frontend with the size set via url parameters. The second use case is as a library to serve properly scaled versions of our images to the frontend to reduce page load size. 

### Scripts
- Install: npm install
- Build: npm run build
- Lint: npm run lint
- Prettify: npm run prettify
- Run unit tests: npm run test
- Start server: npm run start


## How to build and start the server
The project can be built and run in the following ways
### 1. Install all dependencies 
`npm install`

### 2. Build
`npm run build`

This command will build the typeScript code into JavaScript and save them in the `./build` folder.

### 3. Start the Server
`npm run start`

### Usage
The server will listen on port 3000:

#### Brief instructions
http://localhost:3000/

#### Endpoint to resize images
http://localhost:3000/api/images

Expected query arguments are:
- filename: Available filenames are:
  - encenadaport
  - icelandwaterfall
  - palmtunnel
  - santamonica
- width: numerical pixel value > 0
- height: numerical pixel value > 0

#### Example 1
http://localhost:3000/api/images
Will display a hint and list available image names

#### Example 2
http://localhost:3000/api/images?filename=encenadaport&width=200&height=200
Will scale the fjord image to 200 by 200 pixels and store the resulting image.
On subsequent calls will serve the resized image instead of resizing the
original again.

#### Example 3
http://localhost:3000/api/images?filename=encenadaport&width=-200&height=200
Invalid width parameter that will be hinted to.

#### Example 4
http://localhost:3000/api/images?filename=encenadaport&width=200
Missing height parameter that will be hinted to.

### Notes
- Images are served from `./full`. Further images with the extension
  can be put into that directory, but the filetype is not checked
  (not required in exercise).
- Image thumbs will be stored in `./thumb` and can be deleted from
  there to verify that in that case they will be re-created on subsequent calls
  to the same endpoint.