---
title: "Project-Optimization of LiveChess2FEN on Nvidia Jetson Nano"
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
  </style>

  <h2 style="color: var(--neon-yellow); text-align: center;"><b>Optimization of live chess detection on Nvidia Jetson Nano</b></h2>
  
  <h3 style="color: var(--neon-yellow);"><b>1.Goal and Conclusion</b></h3>
  <h4>
      Goal of this project is to implement and deploy LiveChess2FEN(A CNN-based live chess detection) on a Nvidia Jetson Nano, and try to find optimization and acceleartion to improve overall performance.<br><br>
      Based on original research, I've accomplished several tasks in this project, such as model training, deploying the model, and optimization. Despite investing considerable time and effort, I haven't been able to surpass the results of the original research due to limitations in my ability and time. Yet, this project has been a valuable learning experience for me
  </h4>
  <h3 style="color: var(--neon-yellow);"><b>2.An overview of LiveChess2FEN(LC2F)<br>For more information, please refer to the original research paper <a style="color: var(--neon-pink);" href="https://arxiv.org/abs/2012.06858">here</a>.</b></h3>
  <ol style="font-size: 19.5px;" type="I">
    <li>
      <b><i><span style="color: var(--neon-purple);">Why and How</span></i></b><br>
      Automatic digitization of chess games is of great interest for players who want to broadcast their games online or analyze their games with <span style="color: var(--neon-pink);">chess engines</span>.
      Although previous work has shown promising results, the recognition accuracy and latency still require further enhancements to enable practical and cost-effective deployment.
      The research group has investigated implementation on an Nvidia Jetson Nano, accelerating the chessboard's detection algorithm, analyzing different CNNs for chess piece classification, and finding efficient mapping strategies on the embeded system.
      The result is a framework that can automatically digitize a chess position from an image in less than 1 second with 92% accuracy in classifying the pieces and 95% accuracy in detecting the board.
    </li>
  </ol>
  There's two aspects to divide the chess detection problem.
  1. Computer vision wise.
  2. Machine Learning wise.
</div>
