import React from "react";

export default function EnjoyTokApp() {
  const [selectedVideo, setSelectedVideo] = React.useState(null);

  const videos = [
    {
      id: 1,
      user: "Enjoy Tok",
      caption: "Bienvenue sur Enjoy Tok 🔥",
      video: "https://www.w3schools.com/html/mov_bbb.mp4",
    },
    {
      id: 2,
      user: "Enjoy Creator",
      caption: "Partage tes meilleures vidéos ⚽",
      video: "https://www.w3schools.com/html/movie.mp4",
    },
  ];

  const handleVideoUpload = (event) => {
    const file = event.target.files[0];

    if (file) {
      const videoURL = URL.createObjectURL(file);

      videos.unshift({
        id: Date.now(),
        user: "Enjoy User",
        caption: "New uploaded video 🔥",
        video: videoURL,
      });

      setSelectedVideo(videoURL);
    }
  };

  const aiFeatures = [
    "AI Recommendation",
    "HD Upload",
    "Live Streaming",
    "Creator Earnings",
    "Private Chat",
    "Fast Loading Videos",
  ];

  return (
    <div className="relative">
      <div className="fixed inset-0 z-30 bg-black/90 flex items-center justify-center px-4">
        <div className="bg-zinc-900 border border-red-500/30 rounded-3xl p-6 w-full max-w-sm shadow-2xl shadow-red-500/20">
          <div className="text-center mb-6">
            <h1 className="text-3xl font-bold text-red-500">
              Enjoy Tok
            </h1>

            <p className="text-gray-400 text-sm mt-2">
              Watch • Create • Share
            </p>
          </div>

          <div className="flex flex-col gap-4">
            <input
              type="email"
              placeholder="Email"
              className="bg-black border border-white/10 rounded-2xl px-4 py-3 outline-none text-white"
            />

            <input
              type="password"
              placeholder="Password"
              className="bg-black border border-white/10 rounded-2xl px-4 py-3 outline-none text-white"
            />

            <label className="bg-red-500 py-3 rounded-2xl font-bold text-white shadow-lg shadow-red-500/40 cursor-pointer text-center">
              Upload Video
              <input
                type="file"
                accept="video/*"
                className="hidden"
                onChange={handleVideoUpload}
              />
            </label>

            <button className="bg-white/10 py-3 rounded-2xl font-bold border border-white/10 text-white">
              Login
            </button>

            <button className="bg-white/10 py-3 rounded-2xl font-bold border border-white/10 text-white">
              Create Account
            </button>
          </div>
        </div>
      </div>

      <div className="bg-black min-h-screen text-white overflow-y-scroll snap-y snap-mandatory">
        <div className="fixed top-0 left-0 right-0 z-20 flex items-center justify-between px-4 py-3 bg-black/70 backdrop-blur-sm border-b border-red-500/30">
          <h1 className="text-2xl font-bold text-red-500">
            Enjoy Tok
          </h1>

          <div className="flex gap-2">
            <button className="bg-white/10 px-4 py-2 rounded-full text-sm font-semibold border border-white/20">
              Go Live
            </button>

            <button className="bg-red-500 px-4 py-2 rounded-full text-sm font-semibold shadow-lg shadow-red-500/40">
              Login
            </button>
          </div>
        </div>

        <div className="fixed left-3 top-24 z-20 bg-black/60 border border-white/10 rounded-2xl p-3 backdrop-blur-md w-44">
          <h3 className="font-bold text-sm mb-2 text-red-400">
            Enjoy AI
          </h3>

          <div className="flex flex-col gap-2 text-xs text-gray-200">
            {aiFeatures.map((feature) => (
              <div
                key={feature}
                className="bg-white/10 rounded-lg px-2 py-1"
              >
                {feature}
              </div>
            ))}
          </div>
        </div>

        {videos.map((item) => (
          <div
            key={item.id}
            className="relative h-screen w-full snap-start flex items-center justify-center"
          >
            <video
              src={item.video}
              controls
              autoPlay
              loop
              className="absolute inset-0 h-full w-full object-cover"
            />

            <div className="absolute bottom-24 left-4 z-10 max-w-xs">
              <h2 className="font-bold text-lg">
                @{item.user}
              </h2>

              <p className="text-sm mt-2">
                {item.caption}
              </p>
            </div>

            <div className="absolute right-4 bottom-24 flex flex-col items-center gap-5 z-10">
              <button className="bg-white/20 p-3 rounded-full text-xl">
                ❤️
              </button>

              <button className="bg-white/20 p-3 rounded-full text-xl">
                💬
              </button>

              <button className="bg-white/20 p-3 rounded-full text-xl">
                📤
              </button>
            </div>
          </div>
        ))}

        <div className="fixed bottom-0 left-0 right-0 bg-black border-t border-gray-800 flex justify-around py-4 text-sm">
          <button>🏠 Home</button>
          <button>🔍 Discover</button>
          <button className="bg-red-500 px-4 py-1 rounded-full">
            ＋
          </button>
          <button>📩 Inbox</button>
          <button>👤 Profile</button>
          <button>💰 Earn</button>
        </div>
      </div>
    </div>
  );
}
