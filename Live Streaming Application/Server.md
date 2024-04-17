```java

private Database database;

public class VideoConsumingService {
	public int seekTime(String userId, String videoId) {
		WatchedVideo watchedvideo = database.getWatchedVideo(userId,videoId);
		return watchedVideo.getSeekTime();
	}
}

class VideoService {
	private FileSystem fileSystem;
	public Frame getFrame(String videoId, int timestamp) {
		Video video = fileSystem.getVideo(videoId);
		return video.getFrame(timestamp);
	}
}

class FileSystem {

	public Video getVideo(String videoId) {
		return null;
	}
}

// dummy database
class Database {
	public WatchedVideo getWatchedVideo(String userId, String videoId) {
		return null; 
	}
}

class Video {
	String id; 
	Frame[] frames; 
	String jsonMetadata;

	public Frame getFrame(int timestamp) {
		for(int i=0;i<frames.length;i++) {
			// lets assume the frame is of 10sec = frameTime
			// If we pass 57 sec timestamp
			// It should play 50s to 60s of frame
			// thats why the if case
			// 50<=57 and 50+10=60>57
			if(frames[i].startTimestamp<=timestamp && frames[i].endTimestamp>timestmap)
				return frames[i]
		}
		throw new IndexOutOfBoundsException();
	}
	
}

class Frame {
	public static int frameTime = 10;
	byte[] bytes;
	int Starttimestamp;
	int endTimestamp;
}

class User {
	String id;
	String name;
	String email;

	public String getId() {
		return id;
	}
}

class WatchedVideo {

	String id;
	String videoId;
	String userId;
	int seekTime;

	public int getSeekTime() {
		return seekTime();
	}
}

```