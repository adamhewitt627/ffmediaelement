# FFME: *WPF MediaElement Alternative*

## Overview
FFME is a close drop-in replacement for <a href="https://msdn.microsoft.com/en-us/library/system.windows.controls.mediaelement(v=vs.110).aspx">Microsoft's WPF MediaElement Control</a>. While the standard MediaElement uses DirectX (DirectShow) for media playback, FFME uses <a href="http://ffmpeg.org/">FFmpeg</a> to read and decode audio and video. This means that for those of you who want to support stuff like HLS playback, or just don't want to go through the hassle of installing codecs on client machines, using FFME *might* be the answer.

## Compiling, Running and Testing
*Please note that I am unable to distribute FFmpeg's binaries because I don't know if I am allowed to do so. Follow the instructions below to compile, run and test FFME*

1. Clone this repository.
2. Before you open the solution, please make sure you download the FFmpeg win32-shared binaries from <a href="http://ffmpeg.zeranoe.com/builds/win32/shared/ffmpeg-2.8.2-win32-shared.7z">Zeranoe FFmpeg Builds</a>.
3. Extract the contents of the <code>7z</code> file you just downloaded and locate the <code>bin</code> folder.
4. You should see 3 <code>exe</code> files and 8 <code>dll</code> files. Select and copy all of them.
5. Now paste all 11 files from the prior step onto the following folder (inside the cloned repository): <code>{repositiories root}\ffmedialement\Unosquare.FFmpegMediaElement\ffmpeg32</code>.
6. Open the solution and set the <code>Unosquare.FFmpegMediaElement.Tests</code> project as the startup project. You can do this by right clicking on the project and selecting <code>Set as startup project</code>
7. Click on <code>Start</code> to run the project.
8. You should see a very simplistic media player. Enter a URL or a path to a file in the textbox at the top of the window and then click on <code>Open</code>.
9. The file or URL should play immediately.
10. You can use the resulting compiled assembly in your project without further dependencies FFME is entirely self-contained. The locations of the compiled FFME assembly, depending on your build configuration are either <code>...\ffmedialement\Unosquare.FFmpegMediaElement\bin\Debug\Unosquare.FFmpegMediaElement.dll</code> or <code>...\ffmedialement\Unosquare.FFmpegMediaElement\bin\Release\Unosquare.FFmpegMediaElement.dll</code>

## Using FFME in your Project
1. Create a new WPF application
2. Add a reference to <code>Unosquare.FFmpegMediaElement.dll</code>
3. In your <code>MainForm.xaml</code>, add the namespace: <code>xmlns:ffme="clr-namespace:Unosquare.FFmpegMediaElement;assembly=Unosquare.FFmpegMediaElement"</code>
4. Finally, create an instance of the FFME control in your <code>MainForm.xaml</code> as follows: `<ffme:MediaElement x:Name="MediaEl" Background="Gray" LoadedBehavior="Play" UnloadedBehavior="Manual" />`

*The Unosquare.FFmpegMediaElement.Tests project shows most common usages*

## Thanks
*(In no particular order)*
- To the <a href="http://ffmpeg.org/">FFmpeg team</a> for making the Swiss Army Knife of media.
- To Kyle Schwarz for creating and making <a href="http://ffmpeg.zeranoe.com/builds/">Zeranoe FFmpeg builds available to everyone</a>.
- To the <a href="https://github.com/naudio/NAudio">NAudio</a> team for making the best audio library out there for .NET
- To Ruslan Balanukhin for his FFmpeg interop bindings generator tool: <a href="https://github.com/Ruslan-B/FFmpeg.AutoGen">FFmpeg.AutoGen</a>.
- To Martin Bohme for his <a href="http://dranger.com/ffmpeg/">excellent tutorial</a> on creating a video player with FFmpeg.

## Similar Projects
- <a href="https://github.com/Microsoft/FFmpegInterop">Microsoft FFmpeg Interop</a>
- <a href="https://github.com/Sascha-L/WPF-MediaKit">WPF-MediaKit</a>
- <a href="https://libvlcnet.codeplex.com/">LibVLC.NET</a>

## License
- The NAudio portion of this library <code>Unosquare.FFmpegMediaElement\NAudio</code> is distributed under Ms-PL. Please see <a href="https://github.com/unosquare/ffmedialement/blob/master/Unosquare.FFmpegMediaElement/NAudio/LICENSE.txt">LICENSE.txt</a>.
- Code generated by the FFmpeg.Autogen tool <code>Unosquare.FFmpegMediaElement\FFmpeg.Autogen</code> does not specify a license by the tool's author.
- The source code of the FFME project excluding the items above is distributed under the Ms-PL.
