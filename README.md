# Proyecto-Final
Envia tus mensajes a la entidades que descienden de las alturas 
import React, { useState } from 'react';

export default function CelestialCommunicator() {
  const [message, setMessage] = useState('');
  const [sentMessages, setSentMessages] = useState<string[]>([]);
  const [displayMessage, setDisplayMessage] = useState('');

  const handleInputChange = (e: React.ChangeEvent<HTMLTextAreaElement>) => {
    setMessage(e.target.value);
  };

  const handleSendMessage = () => {
    if (message.trim() !== '') {
      setSentMessages([...sentMessages, message]);
      setDisplayMessage(message); // Display the message right after sending
      setMessage(''); // Clear the input
    }
  };

  return (
    <div className="flex flex-col items-center justify-center min-h-screen bg-gray-100">
      <h1 className="text-3xl font-semibold text-gray-800 mb-8">Celestial Communicator</h1>

      {/* Message Input Area */}
      <div className="w-full max-w-md p-6 bg-white rounded-lg shadow-md">
        <label htmlFor="message" className="block text-gray-700 text-sm font-bold mb-2">
          Your Message:
        </label>
        <textarea
          id="message"
          className="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline mb-4"
          rows={4}
          placeholder="Enter your message for the entities..."
          value={message}
          onChange={handleInputChange}
        ></textarea>

        {/* Send Button */}
        <button
          className="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded focus:outline-none focus:shadow-outline"
          onClick={handleSendMessage}
        >
          Send Message
        </button>
      </div>

      {/* Display Sent Messages */}
      {sentMessages.length > 0 && (
        <div className="mt-8 w-full max-w-md">
          <h2 className="text-xl font-semibold text-gray-800 mb-4">Sent Message:</h2>
          <div className="bg-gray-200 p-4 rounded-md">
            <p className="text-gray-700">{displayMessage}</p>
          </div>
        </div>
      )}

      {/* Empty Space for Visual Balance */}
      <div className="mt-8"></div>
    </div>
  );
}
