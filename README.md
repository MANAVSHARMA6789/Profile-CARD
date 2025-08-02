App.css
   /* src/App.css */
   body {
     margin: 0;
     font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
     background-color: #f5f5f5; /* Light gray background */
   }

   .app {
     display: flex;
     justify-content: center;
     align-items: center;
     min-height: 100vh; /* Full height of the viewport */
   }
   App.js
   // src/App.js
import React from 'react';
import ProfileCard from './ProfileCard';
import './App.css';

function App() {
  const user = {
    name: 'John Doe',
    email: 'john.doe@example.com',
    bio: 'Web Developer with a passion for creating beautiful and functional user experiences.',
    imageUrl: 'https://placehold.co/100x100/3b82f6/ffffff?text=Profile',
  };

  return (
    <div className="app">
      <ProfileCard 
        initialName={user.name} 
        initialEmail={user.email} 
        initialBio={user.bio} 
        initialImageUrl={user.imageUrl} 
      />
    </div>
  );
}
App.test.js 
import { render, screen } from '@testing-library/react';
import App from './App';

test('renders learn react link', () => {
  render(<App />);
  const linkElement = screen.getByText(/learn react/i);
  expect(linkElement).toBeInTheDocument();
});
index.css
body {
  margin: 0;
  font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', 'Roboto', 'Oxygen',
    'Ubuntu', 'Cantarell', 'Fira Sans', 'Droid Sans', 'Helvetica Neue',
    sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

code {
  font-family: source-code-pro, Menlo, Monaco, Consolas, 'Courier New',
    monospace;
}
index.js
import React from 'react';
import ReactDOM from 'react-dom/client';
import './index.css';
import App from './App';
import reportWebVitals from './reportWebVitals';

const root = ReactDOM.createRoot(document.getElementById('root'));
root.render(
  <React.StrictMode>
    <App />
  </React.StrictMode>
);

// If you want to start measuring performance in your app, pass a function
// to log results (for example: reportWebVitals(console.log))
// or send to an analytics endpoint. Learn more: https://bit.ly/CRA-vitals
reportWebVitals();
ProfileCard.css
/* src/ProfileCard.css */
.profile-card {
  background: white;
  border-radius: 10px;
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
  padding: 20px;
  text-align: center;
  width: 300px;
  margin: 20px auto;
}

.profile-picture {
  width: 100px;
  height: 100px;
  border-radius: 50%;
  margin-bottom: 15px;
}

.profile-name {
  margin: 0;
  font-size: 24px;
  color: #333;
}

.profile-email {
  margin: 5px 0;
  color: #666;
}

.profile-bio {
  margin: 10px 0;
  color: #555;
}

.edit-button {
  padding: 10px 15px;
  background-color: #3b82f6;
  color: white;
  border: none;
  border-radius: 5px;
  cursor: pointer;
  transition: background-color 0.3s;
}

.edit-button:hover {
  background-color: #2563eb;
}
ProfileCard.js
// src/ProfileCard.js
import React, { useState } from 'react';
import './ProfileCard.css';

const ProfileCard = ({ initialName, initialEmail, initialBio, initialImageUrl }) => {
  const [isEditing, setIsEditing] = useState(false);
  const [name, setName] = useState(initialName);
  const [email, setEmail] = useState(initialEmail);
  const [bio, setBio] = useState(initialBio);
  const [imageUrl, setImageUrl] = useState(initialImageUrl);

  const handleEditToggle = () => {
    setIsEditing(!isEditing);
  };

  const handleSave = () => {
    // Here you can add logic to save the updated profile
    setIsEditing(false);
  };

  return (
    <div className="profile-card">
      {isEditing ? (
        <div>
          <input
            type="text"
            value={name}
            onChange={(e) => setName(e.target.value)}
            placeholder="Name"
          />
          <input
            type="email"
            value={email}
            onChange={(e) => setEmail(e.target.value)}
            placeholder="Email"
          />
          <textarea
            value={bio}
            onChange={(e) => setBio(e.target.value)}
            placeholder="Bio"
          />
          <input
            type="text"
            value={imageUrl}
            onChange={(e) => setImageUrl(e.target.value)}
            placeholder="Image URL"
          />
          <button onClick={handleSave}>Save</button>
        </div>
      ) : (
        <div>
          <img src={imageUrl} alt={`${name}'s profile`} className="profile-picture" />
          <h2 className="profile-name">{name}</h2>
          <p className="profile-email">{email}</p>
          <p className="profile-bio">{bio}</p>
          <button className="edit-button" onClick={handleEditToggle}>
            Edit Profile
          </button>
        </div>
      )}
    </div>
  );
};

export default ProfileCard;
reportWebVitals.js
const reportWebVitals = onPerfEntry => {
  if (onPerfEntry && onPerfEntry instanceof Function) {
    import('web-vitals').then(({ getCLS, getFID, getFCP, getLCP, getTTFB }) => {
      getCLS(onPerfEntry);
      getFID(onPerfEntry);
      getFCP(onPerfEntry);
      getLCP(onPerfEntry);
      getTTFB(onPerfEntry);
    });
  }
};

export default reportWebVitals;
setupTests.js
// jest-dom adds custom jest matchers for asserting on DOM nodes.
// allows you to do things like:
// expect(element).toHaveTextContent(/react/i)
// learn more: https://github.com/testing-library/jest-dom
import '@testing-library/jest-dom';


export default App;

   
