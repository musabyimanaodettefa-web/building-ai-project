# Smart Attendance Assistant

Building AI course project

## Summary
This project proposes an AI-based attendance system that uses face recognition to automatically record student attendance in classrooms. It reduces manual work for teachers and improves accuracy and transparency in schools.

## Background
In many schools, attendance is still taken manually, which is time-consuming and prone to errors. Teachers lose valuable teaching time, and records can be inaccurate. This project is motivated by the need to simplify attendance management using AI technology.

## How is it used?
Teachers use a camera or mobile device to capture classroom images. The system detects and recognizes students' faces and marks attendance automatically. Students and school administrators benefit from accurate records.

## Data sources and AI methods
The system uses image data collected with consent from students. Face recognition techniques and machine learning models such as convolutional neural networks (CNNs) are used for identification.

## Challenges
The system does not solve issues related to poor lighting, camera quality, or students not facing the camera. Privacy and data protection must be handled carefully.

## What next?
The project can be expanded by adding real-time attendance, mobile app integration, and emotion or engagement analysis.

## Acknowledgments
Inspired by the Building AI course by the University of Helsinki and Reaktor.
// Example: Safe student data fetching and attendance marking

// Function to fetch student data safely
async function fetchStudents() {
  try {
    // Replace with your actual API endpoint
    const response = await axios.get('/api/students'); 
    
    // Optional chaining + fallback to empty array
    const students = response?.data || []; 
    console.log("Fetched students:", students);
    return students;

  } catch (error) {
    console.error("Failed to fetch students:", error);
    return []; // fallback to empty list if error occurs
  }
}

// Function to mark attendance based on detected faces
async function markAttendance(detectedFaces) {
  const students = await fetchStudents();

  detectedFaces.forEach(face => {
    // Match detected face to student by unique ID
    const student = students.find(s => s.id === face.id);

    if (student) {
      student.attendance = true;
      console.log(`Marked attendance for ${student.name}`);
    } else {
      console.log("Face not recognized in student list:", face.id);
    }
  });

  return students; // return updated list with attendance
}

// Example usage: detectedFaces from your face recognition system
const detectedFaces = [
  { id: 101, name: "Alice" },
  { id: 102, name: "Bob" },
];

// Mark attendance safely
markAttendance(detectedFaces).then(updatedStudents => {
  console.log("Updated student attendance:", updatedStudents);
});


