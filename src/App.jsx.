import React, { useState, useRef, useEffect } from "react";
import { Heart, MessageCircle, Send, Plus, X, Bookmark, Image as ImageIcon, Film } from "lucide-react";

const INITIAL_POSTS = [
  {
    id: 1,
    user: "aziza.k",
    avatar: "https://picsum.photos/seed/aziza/100/100",
    image: "https://picsum.photos/seed/kadr1/600/600",
    caption: "Buxoro kechqurun 🌇 rangi ajoyib edi",
    likes: 128,
    liked: false,
    saved: false,
    frame: "12A",
    comments: [
      { user: "shaxzod", text: "juda chiroyli!" },
      { user: "nodira.m", text: "qayerda tushirilgan?" },
    ],
  },
  {
    id: 2,
    user: "javlon_photo",
    avatar: "https://picsum.photos/seed/javlon/100/100",
    image: "https://picsum.photos/seed/kadr2/600/600",
    caption: "Tog'lar sukunati. Chorvoq tomonlarida.",
    likes: 342,
    liked: true,
    saved: false,
    frame: "13A",
    comments: [{ user: "aziza.k", text: "menam borgim keldi 😍" }],
  },
  {
    id: 3,
    user: "malika.uz",
    avatar: "https://picsum.photos/seed/malika/100/100",
    image: "https://picsum.photos/seed/kadr3/600/600",
    caption: "Yangi kofe joyi ochildi ☕️",
    likes: 76,
    liked: false,
    saved: true,
    frame: "14A",
    comments: [],
  },
];

const STORIES = [
  { user: "siz", avatar: "https://picsum.photos/seed/you/100/100", isYou: true },
  { user: "aziza.k", avatar: "https://picsum.photos/seed/aziza/100/100" },
  { user: "javlon_photo", avatar: "https://picsum.photos/seed/javlon/100/100" },
  { user: "malika.uz", avatar: "https://picsum.photos/seed/malika/100/100" },
  { user: "otabek", avatar: "https://picsum.photos/seed/otabek/100/100" },
  { user: "dilnoza", avatar: "https://picsum.photos/seed/dilnoza/100/100" },
];

function Sprockets() {
  return (
    <div className="flex justify-between px-3">
      {Array.from({ length: 14 }).map((_, i) => (
        <div key={i} className="w-1.5 h-1.5 rounded-[2px] bg-[#0F0E0D]" />
      ))}
    </div>
  );
}

function PostCard({ post, onLike, onSave, onComment }) {
  const [commentText, setCommentText] = useState("");
  const [showAllComments, setShowAllComments] = useState(false);

  const submitComment = () => {
    if (!commentText.trim()) return;
    onComment(post.id, commentText.trim());
    setCommentText("");
  };

  const visibleComments = showAllComments ? post.comments : post.comments.slice(-1);

  return (
    <div className="bg-[#1C1917] rounded-sm overflow-hidden mb-6 border border-[#2A2724]">
      {/* header */}
      <div className="flex items-center gap-3 px-3 py-3">
        <img src={post.avatar} alt={post.user} className="w-8 h-8 rounded-full object-cover ring-2 ring-[#2FBFA4]/40" />
        <span className="text-[#EDE6DD] text-sm font-semibold tracking-wide">{post.user}</span>
        <span className="ml-auto text-[10px] font-mono text-[#6B655D] tracking-widest">#{post.frame}</span>
      </div>

      {/* sprocket strip top */}
      <div className="bg-[#0F0E0D] py-1"><Sprockets /></div>

      {/* image */}
      <div className="relative bg-black">
        <img src={post.image} alt={post.caption} className="w-full aspect-square object-cover" />
      </div>

      {/* sprocket strip bottom */}
      <div className="bg-[#0F0E0D] py-1"><Sprockets /></div>

      {/* actions */}
      <div className="flex items-center gap-4 px-3 pt-3">
        <button onClick={() => onLike(post.id)} aria-label="Layk bosish" className="active:scale-90 transition-transform">
          <Heart
            size={24}
            className={post.liked ? "fill-[#2FBFA4] text-[#2FBFA4]" : "text-[#EDE6DD]"}
            strokeWidth={1.8}
          />
        </button>
        <MessageCircle size={24} className="text-[#EDE6DD]" strokeWidth={1.8} />
        <Send size={22} className="text-[#EDE6DD]" strokeWidth={1.8} />
        <button onClick={() => onSave(post.id)} aria-label="Saqlash" className="ml-auto active:scale-90 transition-transform">
          <Bookmark size={22} className={post.saved ? "fill-[#E2A33A] text-[#E2A33A]" : "text-[#EDE6DD]"} strokeWidth={1.8} />
        </button>
      </div>

      {/* likes */}
      <div className="px-3 pt-2 text-[#EDE6DD] text-sm font-semibold">{post.likes.toLocaleString()} layk</div>

      {/* caption */}
      <div className="px-3 pt-1 text-sm text-[#EDE6DD]">
        <span className="font-semibold mr-1">{post.user}</span>
        <span className="text-[#C9C1B6]">{post.caption}</span>
      </div>

      {/* comments */}
      <div className="px-3 pt-1 pb-1">
        {post.comments.length > 1 && !showAllComments && (
          <button onClick={() => setShowAllComments(true)} className="text-[#6B655D] text-xs mb-1 block">
            {post.comments.length} ta izohni ko'rish
          </button>
        )}
        {visibleComments.map((c, i) => (
          <div key={i} className="text-sm text-[#C9C1B6]">
            <span className="font-semibold text-[#EDE6DD] mr-1">{c.user}</span>
            {c.text}
          </div>
        ))}
      </div>

      {/* add comment */}
      <div className="flex items-center gap-2 px-3 py-2 border-t border-[#2A2724] mt-1">
        <input
          value={commentText}
          onChange={(e) => setCommentText(e.target.value)}
          onKeyDown={(e) => e.key === "Enter" && submitComment()}
          placeholder="Izoh qoldiring..."
          className="flex-1 bg-transparent text-sm text-[#EDE6DD] placeholder-[#6B655D] outline-none py-1"
        />
        <button
          onClick={submitComment}
          disabled={!commentText.trim()}
          className="text-[#2FBFA4] text-sm font-semibold disabled:text-[#3A3630] disabled:cursor-not-allowed"
        >
          Yuborish
        </button>
      </div>
    </div>
  );
}

function NewPostModal({ onClose, onCreate }) {
  const [caption, setCaption] = useState("");
  const [imageUrl, setImageUrl] = useState("");
  const fileRef = useRef(null);
  const [preview, setPreview] = useState("");

  const handleFile = (e) => {
    const file = e.target.files?.[0];
    if (!file) return;
    const reader = new FileReader();
    reader.onload = () => setPreview(reader.result);
    reader.readAsDataURL(file);
  };

  const create = () => {
    const img = preview || imageUrl || `https://picsum.photos/seed/${Date.now()}/600/600`;
    onCreate({ image: img, caption });
    onClose();
  };

  return (
    <div className="fixed inset-0 bg-black/80 flex items-center justify-center z-50 p-4">
      <div className="bg-[#1C1917] w-full max-w-sm rounded-sm border border-[#2A2724] overflow-hidden">
        <div className="flex items-center justify-between px-4 py-3 border-b border-[#2A2724]">
          <span className="text-[#EDE6DD] font-semibold flex items-center gap-2">
            <Film size={18} className="text-[#2FBFA4]" /> Yangi kadr
          </span>
          <button onClick={onClose}><X size={20} className="text-[#EDE6DD]" /></button>
        </div>

        <div className="p-4 space-y-3">
          <div
            onClick={() => fileRef.current?.click()}
            className="aspect-square bg-[#0F0E0D] border border-dashed border-[#3A3630] rounded-sm flex items-center justify-center cursor-pointer overflow-hidden"
          >
            {preview ? (
              <img src={preview} alt="Ko'rinish" className="w-full h-full object-cover" />
            ) : (
              <div className="flex flex-col items-center text-[#6B655D] gap-2">
                <ImageIcon size={28} />
                <span className="text-xs">Rasm tanlash uchun bosing</span>
              </div>
            )}
          </div>
          <input ref={fileRef} type="file" accept="image/*" onChange={handleFile} className="hidden" />

          <input
            value={imageUrl}
            onChange={(e) => setImageUrl(e.target.value)}
            placeholder="yoki rasm havolasini kiriting (URL)"
            className="w-full bg-[#0F0E0D] text-sm text-[#EDE6DD] placeholder-[#6B655D] outline-none px-3 py-2 rounded-sm border border-[#2A2724]"
          />

          <textarea
            value={caption}
            onChange={(e) => setCaption(e.target.value)}
            placeholder="Izoh yozing..."
            rows={3}
            className="w-full bg-[#0F0E0D] text-sm text-[#EDE6DD] placeholder-[#6B655D] outline-none px-3 py-2 rounded-sm border border-[#2A2724] resize-none"
          />

          <button
            onClick={create}
            className="w-full bg-[#2FBFA4] text-[#0F0E0D] font-semibold text-sm py-2.5 rounded-sm active:scale-[0.98] transition-transform"
          >
            Joylash
          </button>
        </div>
      </div>
    </div>
  );
}

function StoryViewer({ story, onClose }) {
  if (!story) return null;
  return (
    <div className="fixed inset-0 bg-black flex items-center justify-center z-50" onClick={onClose}>
      <div className="w-full max-w-sm h-[85vh] relative">
        <div className="absolute top-2 left-2 right-2 h-0.5 bg-white/30 rounded-full">
          <div className="h-full w-full bg-[#2FBFA4] rounded-full" />
        </div>
        <div className="absolute top-5 left-3 flex items-center gap-2">
          <img src={story.avatar} className="w-7 h-7 rounded-full object-cover" alt={story.user} />
          <span className="text-white text-sm font-semibold">{story.user}</span>
        </div>
        <button className="absolute top-5 right-3" onClick={onClose}>
          <X size={22} className="text-white" />
        </button>
        <img src={story.avatar.replace("100/100", "600/900")} className="w-full h-full object-cover" alt="hikoya" />
      </div>
    </div>
  );
}

export default function KadrApp() {
  const [posts, setPosts] = useState(INITIAL_POSTS);
  const [showNewPost, setShowNewPost] = useState(false);
  const [activeStory, setActiveStory] = useState(null);

  // Telegram Mini App bo'lib ishga tushganda: to'liq ekranga yoyish,
  // sarlavha rangini ilova foniga moslash. Oddiy brauzerda bu qism
  // e'tiborsiz qoladi (window.Telegram mavjud bo'lmasa).
  useEffect(() => {
    const tg = window.Telegram?.WebApp;
    if (!tg) return;
    tg.ready();
    tg.expand();
    tg.setHeaderColor?.("#121110");
    tg.setBackgroundColor?.("#121110");
  }, []);

  const toggleLike = (id) => {
    setPosts((prev) =>
      prev.map((p) =>
        p.id === id ? { ...p, liked: !p.liked, likes: p.liked ? p.likes - 1 : p.likes + 1 } : p
      )
    );
  };

  const toggleSave = (id) => {
    setPosts((prev) => prev.map((p) => (p.id === id ? { ...p, saved: !p.saved } : p)));
  };

  const addComment = (id, text) => {
    setPosts((prev) =>
      prev.map((p) => (p.id === id ? { ...p, comments: [...p.comments, { user: "siz", text }] } : p))
    );
  };

  const createPost = ({ image, caption }) => {
    const nextFrame = `${15 + posts.length}A`;
    setPosts((prev) => [
      {
        id: Date.now(),
        user: "siz",
        avatar: "https://picsum.photos/seed/you/100/100",
        image,
        caption: caption || "",
        likes: 0,
        liked: false,
        saved: false,
        frame: nextFrame,
        comments: [],
      },
      ...prev,
    ]);
  };

  return (
    <div className="min-h-screen bg-[#121110] flex justify-center font-sans">
      <div className="w-full max-w-md">
        {/* top bar */}
        <div className="sticky top-0 z-10 bg-[#121110]/95 backdrop-blur border-b border-[#2A2724] px-4 py-3 flex items-center justify-between">
          <div className="flex items-center gap-1.5">
            <Film size={20} className="text-[#2FBFA4]" strokeWidth={2} />
            <span className="text-[#EDE6DD] text-xl tracking-wide" style={{ fontFamily: "Georgia, serif", fontWeight: 700 }}>
              KADR
            </span>
          </div>
          <button
            onClick={() => setShowNewPost(true)}
            className="flex items-center gap-1 text-[#0F0E0D] bg-[#E2A33A] text-xs font-semibold px-3 py-1.5 rounded-sm active:scale-95 transition-transform"
          >
            <Plus size={14} strokeWidth={2.5} /> Kadr
          </button>
        </div>

        {/* stories */}
        <div className="flex gap-4 px-4 py-4 overflow-x-auto border-b border-[#2A2724]">
          {STORIES.map((s, i) => (
            <button
              key={i}
              onClick={() => (s.isYou ? setShowNewPost(true) : setActiveStory(s))}
              className="flex flex-col items-center gap-1 shrink-0"
            >
              <div
                className={`w-14 h-14 rounded-full p-[2px] ${
                  s.isYou ? "border-2 border-dashed border-[#6B655D]" : "bg-gradient-to-tr from-[#2FBFA4] to-[#E2A33A]"
                }`}
              >
                <div className="bg-[#121110] rounded-full p-[2px] w-full h-full">
                  <img src={s.avatar} className="w-full h-full rounded-full object-cover" alt={s.user} />
                </div>
              </div>
              <span className="text-[10px] text-[#C9C1B6] max-w-[56px] truncate">{s.isYou ? "Siz" : s.user}</span>
            </button>
          ))}
        </div>

        {/* feed */}
        <div className="px-3 pt-4">
          {posts.map((post) => (
            <PostCard key={post.id} post={post} onLike={toggleLike} onSave={toggleSave} onComment={addComment} />
          ))}
        </div>
      </div>

      {showNewPost && <NewPostModal onClose={() => setShowNewPost(false)} onCreate={createPost} />}
      <StoryViewer story={activeStory} onClose={() => setActiveStory(null)} />
    </div>
  );
}
