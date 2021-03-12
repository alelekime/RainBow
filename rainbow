import SpriteKit
import AVFoundation

setUpLiveView()

var audioPlayer: AVAudioPlayer?

func playSound(sound: String, type: String) {
    if let path = Bundle.main.path(forResource: sound, ofType: type) {
        do {
            audioPlayer = try AVAudioPlayer(contentsOf: URL(fileURLWithPath: path))
            audioPlayer?.play()
            audioPlayer?.volume = 0.5
        } catch {
            print("ERROR")
        }
    }
}

for album in albums {
    
    let polygon = Graphic.rectangle(width: 65, height: 1000, cornerRadius: 0, color: album.3)
    scene.place(polygon, at: album.0)
    polygon.onTouch {
        if  polygon.xScale == 1 {
            polygon.zPosition = 1
            playSound(sound: album.music, type: "mp3")
        }else{
            audioPlayer?.stop()
        }
        
        polygon.run(SKAction.scale(to: polygon.xScale == 1 ? 25 : 1, duration: 0.3)){
            if  polygon.xScale == 1 {
                polygon.zPosition = 0
            }
        }
        
        let image = album.1
        image.zPosition = 2
        scene.place(image, at: album.2)
        image.scale(to: polygon.xScale == 1 ? 1 : 0, duration: image.xScale == 0 ? 0.3: 0.1)
    }
}
