---
title: "[Project] Optimization of LiveChess2FEN on Nvidia Jetson Nano(WIP)"
date: "Aug 13, 2023"
---
<div>

  <style>
    /* Neon colors */
    :root {
      --neon-yellow: #f4d03f;
      --neon-pink: #f62459;
      --neon-blue: #0dc9f7;
      --neon-green: #39ff14;
      --neon-purple: #586AE2;
    }
    ul.custom-list {
    list-style-type: upper-alpha;
    }
  </style>
  <h3 style="color: var(--neon-pink);"><b>*This is an overview page. If you want to see more details, please visit <a href="https://arxiv.org/pdf/2012.06858.pdf">original paper</a> and my <a href="https://drive.google.com/file/d/1sPUws4-nrXC6g3z8mkLZowwr9qup-_4D/view">google drive</a> .</b></h3>
  
  <h3 style="color: var(--neon-yellow);"><b>【About】</b></h3>
    <h4>
      Goal of this project is to implement and deploy LiveChess2FEN (A CNN-based live chess detection) on a Nvidia Jetson Nano, and try to find optimization and acceleration to improve overall performance.
    </h4>

  <h3 style="color: var(--neon-yellow);"><b>【Why】</b></h3>
    <h4>
      Automatic digitization of chess games is of great interest for players who want to broadcast their games online or analyze their games with chess engines. Although previous work has shown promising results, the recognition accuracy and latency still require further enhancements to enable practical and cost-effective deployment. Optimizing on the Jetson Nano, a platform with limited resources, holds significant relevance. Additionally, the chess automatic digitalization system holds practical applications such as live streaming for chess games.
    </h4>

  <h3 style="color: var(--neon-yellow);"><b>【Methodologies】</b></h3>
    <h4>
      There's three parts of our works.
      <ol>
        <li>
          <span style="color: var(--neon-yellow);">Model Optimization</span><br>
          We used various combinations to find the solution, including Keras + TensorFlow (Native), ONNX Runtime, and TensorRT, among others. Considering the deployment difficulty for users, ONNX Runtime + Keras is our first choice. By leveraging modern tools, we successfully decreased the model loading and operation time.
        </li>
        <li>
          <span style="color: var(--neon-yellow);">Resource reusage</span><br>
          <ul class="custom-list">
            <li>
              <span style="color: var(--neon-pink);">Chessboard detection</span><br>
              We utilize the method outlined in the original paper to detect the corners of the central 6x6 squares. If the result remains consistent (indicating that the board hasn't been moved), the system can leverage the previous result. This approach is highly effective; we saved approximately 70% of the time by employing it.
            </li>
            <li> 
              <span style="color: var(--neon-pink);">Chess piece recognition</span><br>
              We utilize chess rules to assist the system in detecting chess pieces. For instance, a king can move one square horizontally, vertically, or diagonally. By leveraging this information, the system can achieve greater accuracy. Additionally, we analyze changes in probability to identify which chess piece has been moved. The stricter the change in probability, the higher the likelihood that it represents the moved piece. However, this approach did not yield significant improvement, saving only around 1% of time.
            </li>
          </ul>
        </li>
        <li>
          <span style="color: var(--neon-yellow);">I/O delay</span><br>
          During the experiment, we discovered a significant hardware delay of 7 seconds. As a solution, we employed OpenCV and Python to implement our own camera command, effectively reducing the delay to 2-3 seconds.
        </li>
      </ol>
    </h4>

  <h3 style="color: var(--neon-yellow);"><b>【Result】</b></h3>
    <h4>
      Based on original research, I've accomplished several tasks in this project, such as model training, deploying the model, and optimization. Despite investing considerable time and effort, I haven't been able to surpass the results of the original research due to limitations in my ability and time. Yet, this project has been a valuable learning experience for me.
    </h4>
</div>
