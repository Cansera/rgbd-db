# RGB-D Image Dataset

This repository contains skeleton files and documentation for Cansera's Azure Kinect RGB-D image dataset.

The dataset includes:

- 64 skeleton JSON files available in this repository
- 64 RGB-D video recordings available on a shared OneDrive
- Documentation explaining how the dataset was created in this README.md

## Participants Demographics

n = 64

|                  | Category               | Count |    % |
| ---------------- | ---------------------- | ----- | -----|
| Age              | 18-49                  | 36    | 56.3 |
|                  | 50-59                  | 17    | 26.6 |
|                  | 60-69                  | 6     | 9.4  |
|                  | 70+                    | 5     | 7.8  |
| Sex              | Female                 | 36    | 56.3 |
|                  | Male                   | 28    | 43.7 |
| Race & Ethnicity | African American       | 9     | 14.1 |
|                  | Asian                  | 12    | 18.8 |
|                  | Caucasian              | 22    | 34.4 |
|                  | Hispanics              | 21    | 32.8 |
| IBW              | under IBW              | 19    | 29.7 |
|                  | IBW to IBW + 15%       | 15    | 23.4 |
|                  | IBW + 15% to IBW + 30% | 16    | 25.0 |
|                  | over IBW + 30%         | 14    | 21.9 |


## Collection Methods

### Chair to Table Task Set Up

Participants are asked to perform the chair to table task as follows:

- Participants start seated in the chair and move to the highchair (hight of 30") placed 16" away
- Participants are instructed to move when prompted and wait on the highchair until the end of the recording
- Participants are instructed not to cross legs or arms while seated

### RGB-D Video Recordings

Azure Kinect RGB-D videos are recorded using the [Azure Kinect Recorder k4arecorder.exe](https://docs.microsoft.com/en-us/azure/kinect-dk/azure-kinect-recorder) and last 20 seconds. Recordings are stored in the [Matroska](https://www.matroska.org/) file format with `kmv` file extension. Matroska defines a standard for multimedia container formats used by Azure Kinect to store RGB-D streams.

Recordings can be replayed using the [Azure Kinect Viewer](https://docs.microsoft.com/en-us/azure/kinect-dk/azure-kinect-viewer): start the viewer, click `Open Recording` to load a `kmv` file.

RGB-D videos files are stored in a Cansera OneDrive due to their size. Please contact [nocera@cansera.com](mailto:nocera@cansera.com) for access to the RGB-D videos.

### Skeleton Data

Skeleton JSON files are extracted from the `mkv` recording using the `offline_processor.exe` executable from the [Azure Kinect body tracking SDK](https://docs.microsoft.com/en-us/azure/kinect-dk/body-sdk-setup). Skeleton files are extracted offline for each frame which ensures a constant framerate. Skeleton files are in JSON format as produced by the `offline_processor.exe` and contain the following information:

```plain-text
bone_list: A skeleton includes 32 joints with the joint hierarchy flowing from the center of the body to the extremities. Each connection (bone) links the parent joint with a child joint.

body_id: Each body includes an ID for temporal correlation between frames and the kinematic skeleton.

joint_orientations: relative to the global depth sensor frame of reference

Joint position: relative to the global depth sensor frame of reference. This is the mapping we use:

body.joint_positions[0][0], - body.joint_positions[0][1], body.joint_positions[0][2]: Pelvis coordinates
body.joint_positions[1][0], - body.joint_positions[1][1], body.joint_positions[1][2]: Spine Navel coordinates
body.joint_positions[2][0], - body.joint_positions[2][1], body.joint_positions[2][2]: Spine Chest coordinates
body.joint_positions[3][0], - body.joint_positions[3][1], body.joint_positions[3][2]: Neck coordinates
body.joint_positions[4][0], - body.joint_positions[4][1], body.joint_positions[4][2]: Clavicle Left coordinates
body.joint_positions[5][0], - body.joint_positions[5][1], body.joint_positions[5][2]: Shoulder Left coordinates
body.joint_positions[6][0], - body.joint_positions[6][1], body.joint_positions[6][2]: Elbow Left coordinates
body.joint_positions[7][0], - body.joint_positions[7][1], body.joint_positions[7][2]: Wrist Left coordinates
body.joint_positions[8][0], - body.joint_positions[8][1], body.joint_positions[8][2]: Hand Left coordinates
body.joint_positions[9][0], - body.joint_positions[9][1], body.joint_positions[9][2]: Handtip Left coordinates
body.joint_positions[10][0], - body.joint_positions[10][1], body.joint_positions[10][2]: Thumb Left coordinates
body.joint_positions[11][0], - body.joint_positions[11][1], body.joint_positions[11][2]: Clavicle Right coordinates
body.joint_positions[12][0], - body.joint_positions[12][1], body.joint_positions[12][2]: Shoulder Right coordinates
body.joint_positions[13][0], - body.joint_positions[13][1], body.joint_positions[13][2]: Elbow Right coordinates
body.joint_positions[14][0], - body.joint_positions[14][1], body.joint_positions[14][2]: Wrist Right coordinates
body.joint_positions[15][0], - body.joint_positions[15][1], body.joint_positions[15][2]: Hand Right coordinates
body.joint_positions[16][0], - body.joint_positions[16][1], body.joint_positions[16][2]: Handtip Right coordinates
body.joint_positions[17][0], - body.joint_positions[17][1], body.joint_positions[17][2]: Thumb Right coordinates
body.joint_positions[18][0], - body.joint_positions[18][1], body.joint_positions[18][2]: Hip Left coordinates
body.joint_positions[19][0], - body.joint_positions[19][1], body.joint_positions[19][2]: Knee Left coordinates
body.joint_positions[20][0], - body.joint_positions[20][1], body.joint_positions[20][2]: Ankle Left coordinates
body.joint_positions[21][0], - body.joint_positions[21][1], body.joint_positions[21][2]: Foot Left coordinates
body.joint_positions[22][0], - body.joint_positions[22][1], body.joint_positions[22][2]: Hip Right coordinates
body.joint_positions[23][0], - body.joint_positions[23][1], body.joint_positions[23][2]: Knee Right coordinates
body.joint_positions[24][0], - body.joint_positions[24][1], body.joint_positions[24][2]: Ankle Right coordinates
body.joint_positions[25][0], - body.joint_positions[25][1], body.joint_positions[25][2]: Foot Right coordinates
body.joint_positions[26][0], - body.joint_positions[26][1], body.joint_positions[26][2]: Head coordinates
body.joint_positions[27][0], - body.joint_positions[27][1], body.joint_positions[27][2]: Nose coordinates
body.joint_positions[28][0], - body.joint_positions[28][1], body.joint_positions[28][2]: Eye Left coordinates
body.joint_positions[29][0], - body.joint_positions[29][1], body.joint_positions[29][2]: Ear Left coordinates
body.joint_positions[30][0], - body.joint_positions[30][1], body.joint_positions[30][2]: Eye Right coordinates
body.joint_positions[31][0], - body.joint_positions[31][1], body.joint_positions[31][2]: Ear Right coordinates

frame_id: frame number starting at 0

num_bodies: total number of bodies detected in each frame

timestamp_usec: unix timestamp in microsecond detected in each frame
```
