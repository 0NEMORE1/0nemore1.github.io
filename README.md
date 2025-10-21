
<html lang="th">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Messier Objects Grid - Dark Theme + Lightbox</title>
    <style>
        body {
            font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Helvetica, Arial, sans-serif;
            margin: 0;
            padding: 20px;
            background-color: #1a1a2e;
            color: #e0e0e0;
            line-height: 1.6;
            display: flex;
            flex-direction: column;
            align-items: center;
            min-height: 100vh;
        }
        h1 {
            text-align: center;
            color: #92b8ff;
            margin-bottom: 40px;
            font-size: 2.8em;
            letter-spacing: 1.5px;
            text-shadow: 0 0 10px rgba(146, 184, 255, 0.4);
        }
        .page-subtitle {
            text-align: center;
            margin-top: -25px; 
            margin-bottom: 30px;
        }
        .page-subtitle .slogan {
            font-size: 1.1em;
            font-style: italic;
            color: #d0d0d0; 
            margin: 0;
            padding: 0;
            line-height: 1.4;
        }
         .page-subtitle .copyright {
            font-size: 0.9em;
            color: #8a8aae;
            margin: 8px 0 0 0;
            padding: 0;
            letter-spacing: 0.5px;
        }  .messier-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(280px, 1fr)); 
            gap: 25px;
            max-width: 1400px;
            width: 100%;
            margin: 0 auto;
            padding: 30px;
            background-color: #2c2c4d;
            border-radius: 12px;
            box-shadow: 0 8px 20px rgba(0,0,0,0.4);
        }
        .messier-item {
            background-color: #3b3b5c;
            border: 1px solid #4a4a75;
            border-radius: 10px;
            padding: 20px;
            text-align: center;
            box-shadow: 0 4px 10px rgba(0,0,0,0.25);
            transition: transform 0.2s ease-in-out, box-shadow 0.2s ease-in-out;
        }
        .messier-item:hover {
            transform: translateY(-8px);
            box-shadow: 0 10px 25px rgba(0,0,0,0.4);
            background-color: #4a4a75;
        }
        .messier-item h2 {
            font-size: 2.0em;
            color: #92b8ff;
            margin-top: 0;
            margin-bottom: 8px;
            letter-spacing: 0.5px;
        }
        .messier-item h3 {
            font-size: 1.2em;
            color: #c0c0c0;
            margin-top: 0;
            margin-bottom: 12px;
            font-weight: normal;
        }
        .messier-item p {
            font-size: 0.95em;
            color: #a0a0a0;
            margin-bottom: 8px;
        }
        .messier-item img {
            max-width: 100%;
            height: 180px;
            object-fit: cover;
            border-radius: 8px;
            margin-bottom: 20px;
            border: 2px solid #5a5a8a;
            box-shadow: 0 2px 8px rgba(0,0,0,0.2);
            cursor: zoom-in; 
        }
        .messier-item .info span {
            display: block;
            font-size: 0.88em;
            color: #b0b0b0;
            margin-bottom: 4px;
        }
        .messier-item .common-name {
            font-style: italic;
            color: #d0d0d0;
        }
        .messier-item .no-image {
            display: flex;
            justify-content: center;
            align-items: center;
            height: 180px;
            background-color: #2a2a40;
            color: #7a7a99;
            border-radius: 8px;
            margin-bottom: 20px;
            border: 2px dashed #4a4a75;
            font-size: 1em;
            font-weight: bold;
            letter-spacing: 0.5px;
        }  @media (max-width: 768px) {
            .messier-grid {
                grid-template-columns: repeat(auto-fill, minmax(220px, 1fr));
                padding: 20px;
                gap: 20px;
            }
            h1 {
                font-size: 2.2em;
                margin-bottom: 30px;
            }
            .messier-item h2 {
                font-size: 1.8em;
            }
            .messier-item img, .messier-item .no-image {
                height: 140px;
            }
        }

 @media (max-width: 480px) {
            .messier-grid {
                grid-template-columns: 1fr;
                padding: 15px;
                gap: 15px;
            }
            h1 {
                font-size: 1.8em;
                margin-bottom: 20px;
            }
            .messier-item {
                padding: 15px;
            }
            .messier-item img, .messier-item .no-image {
                height: 120px;
            }
        }
        
       
 .lightbox-overlay {
            display: none; 
            position: fixed; 
            z-index: 1000; 
            left: 0;
            top: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0, 0, 0, 0.9); 
            justify-content: center;
            align-items: center;
            animation: fadeIn 0.3s ease; 
        }
         .lightbox-active {
            display: flex; 
        }
        #lightbox-image {
            max-width: 90vw; 
            max-height: 90vh; 
            object-fit: contain;
            border-radius: 8px;
            box-shadow: 0 0 50px rgba(146, 184, 255, 0.5);
            border: 2px solid #92b8ff;
        }
        .lightbox-close {
            position: absolute;
            top: 20px;
            right: 40px;
            color: #ffffff;
            font-size: 50px;
            font-weight: bold;
            cursor: pointer;
            transition: color 0.2s;
        }
        .lightbox-close:hover {
            color: #92b8ff; 
        }
        @keyframes fadeIn {
            from { opacity: 0; }
            to { opacity: 1; }
        }

    </style>
</head>
<body>
    <h1>Messier Objects Gallery</h1>
    <div class="page-subtitle">
        <p class="slogan">"A chronicle of relentless pursuit: Woraphop Tessarak's journey through the cosmos, 7 Aug 2024 – Present."</p>
        <p class="copyright">&copy; Woraphop Astrophotography</p>
    </div>
    <div class="messier-grid">
        <div class="messier-item">
            <h2>M1</h2>
            <img src="" alt="Crab Nebula" onerror="this.onerror=null;this.style.display='none'; this.parentNode.querySelector('.no-image').style.display='flex';">
            <div class="no-image" style="display: none;">Add Image for M1</div>
            <p class="common-name">Crab Nebula (เนบิวลาปู)</p>
            <div class="info">
                <span>NGC: 1952</span>
                <span>ประเภท: Supernova Remnant</span>
                <span>กลุ่มดาว: Taurus (วัว)</span>
            </div>
        </div>
        <div class="messier-item">
            <h2>M2</h2>
            <img src="" alt="Messier 2" onerror="this.onerror=null;this.style.display='none'; this.parentNode.querySelector('.no-image').style.display='flex';">
            <div class="no-image" style="display: none;">Add Image for M2</div>
            <p class="common-name"></p>
            <div class="info">
                <span>NGC: 7089</span>
                <span>ประเภท: Globular Cluster</span>
                <span>กลุ่มดาว: Aquarius (คนแบกหม้อน้ำ)</span>
            </div>
        </div>
        <div class="messier-item">
            <h2>M3</h2>
            <img src="" alt="Messier 3" onerror="this.onerror=null;this.style.display='none'; this.parentNode.querySelector('.no-image').style.display='flex';">
            <div class="no-image" style="display: none;">Add Image for M3</div>
            <p class="common-name"></p>
            <div class="info">
                <span>NGC: 5272</span>
                <span>ประเภท: Globular Cluster</span>
                <span>กลุ่มดาว: Canes Venatici (หมาล่าเนื้อ)</span>
            </div>
        </div>
        <div class="messier-item">
            <h2>M4</h2>
            <img src="" alt="Messier 4" onerror="this.onerror=null;this.style.display='none'; this.parentNode.querySelector('.no-image').style.display='flex';">
            <div class="no-image" style="display: none;">Add Image for M4</div>
            <p class="common-name"></p>
            <div class="info">
                <span>NGC: 6121</span>
                <span>ประเภท: Globular Cluster</span>
                <span>กลุ่มดาว: Scorpius (แมงป่อง)</span>
            </div>
        </div>
        <div class="messier-item">
            <h2>M5</h2>
            <img src="" alt="Messier 5" onerror="this.onerror=null;this.style.display='none'; this.parentNode.querySelector('.no-image').style.display='flex';">
            <div class="no-image" style="display: none;">Add Image for M5</div>
            <p class="common-name"></p>
            <div class="info">
                <span>NGC: 5904</span>
                <span>ประเภท: Globular Cluster</span>
                <span>กลุ่มดาว: Serpens (งู)</span>
            </div>
        </div>
        <div class="messier-item">
            <h2>M6</h2>
            <img src="" alt="Butterfly Cluster" onerror="this.onerror=null;this.style.display='none'; this.parentNode.querySelector('.no-image').style.display='flex';">
            <div class="no-image" style="display: none;">Add Image for M6</div>
            <p class="common-name">Butterfly Cluster</p>
            <div class="info">
                <span>NGC: 6405</span>
                <span>ประเภท: Open Cluster</span>
                <span>กลุ่มดาว: Scorpius (แมงป่อง)</span>
            </div>
        </div>
        <div class="messier-item">
            <h2>M7</h2>
            <img src="รูปภาพที่เสร็จเเล้ว/M7 13 Oct 2025 17,49 Utc -6 .jpg" alt="Ptolemy Cluster" onerror="this.onerror=null;this.style.display='none'; this.parentNode.querySelector('.no-image').style.display='flex';">
            <div class="no-image" style="display: none;">Add Image for M7</div>
            <p class="common-name">Ptolemy Cluster</p>
            <div class="info">
                <span>NGC: 6475</span>
                <span>ประเภท: Open Cluster</span>
                <span>กลุ่มดาว: Scorpius (แมงป่อง)</span>
            </div>
        </div>
        <div class="messier-item">
            <h2>M8</h2>
            <img src="รูปภาพที่เสร็จเเล้ว/SHO M8-4.jpg" alt="Lagoon Nebula" onerror="this.onerror=null;this.style.display='none'; this.parentNode.querySelector('.no-image').style.display='flex';">
            <div class="no-image" style="display: none;">Add Image for M8</div>
            <p class="common-name">Lagoon Nebula (เนบิวลาทะเลสาบ)</p>
            <div class="info">
                <span>NGC: 6523</span>
                <span>ประเภท: Diffuse Nebula</span>
                <span>กลุ่มดาว: Sagittarius (คนยิงธนู)</span>
            </div>
        </div>
        <div class="messier-item">
            <h2>M9</h2>
            <img src="" alt="Messier 9" onerror="this.onerror=null;this.style.display='none'; this.parentNode.querySelector('.no-image').style.display='flex';">
            <div class="no-image" style="display: none;">Add Image for M9</div>
            <p class="common-name"></p>
            <div class="info">
                <span>NGC: 6333</span>
                <span>ประเภท: Globular Cluster</span>
                <span>กลุ่มดาว: Ophiuchus (คนแบกงู)</span>
            </div>
        </div>
        <div class="messier-item">
            <h2>M10</h2>
            <img src="" alt="Messier 10" onerror="this.onerror=null;this.style.display='none'; this.parentNode.querySelector('.no-image').style.display='flex';">
            <div class="no-image" style="display: none;">Add Image for M10</div>
            <p class="common-name"></p>
            <div class="info">
                <span>NGC: 6254</span>
                <span>ประเภท: Globular Cluster</span>
                <span>กลุ่มดาว: Ophiuchus (คนแบกงู)</span>
            </div>
        </div>
        <div class="messier-item">
            <h2>M11</h2>
            <img src="" alt="Wild Duck Cluster" onerror="this.onerror=null;this.style.display='none'; this.parentNode.querySelector('.no-image').style.display='flex';">
            <div class="no-image" style="display: none;">Add Image for M11</div>
            <p class="common-name">Wild Duck Cluster</p>
            <div class="info">
                <span>NGC: 6705</span>
                <span>ประเภท: Open Cluster</span>
                <span>กลุ่มดาว: Scutum (โล่)</span>
            </div>
        </div>
        <div class="messier-item">
            <h2>M12</h2>
            <img src="" alt="Messier 12" onerror="this.onerror=null;this.style.display='none'; this.parentNode.querySelector('.no-image').style.display='flex';">
            <div class="no-image" style="display: none;">Add Image for M12</div>
            <p class="common-name"></p>
            <div class="info">
                <span>NGC: 6218</span>
                <span>ประเภท: Globular Cluster</span>
                <span>กลุ่มดาว: Ophiuchus (คนแบกงู)</span>
            </div>
        </div>
        <div class="messier-item">
            <h2>M13</h2>
            <img src="" alt="Hercules Globular Cluster" onerror="this.onerror=null;this.style.display='none'; this.parentNode.querySelector('.no-image').style.display='flex';">
            <div class="no-image" style="display: none;">Add Image for M13</div>
            <p class="common-name">Hercules Globular Cluster</p>
            <div class="info">
                <span>NGC: 6205</span>
                <span>ประเภท: Globular Cluster</span>
                <span>กลุ่มดาว: Hercules (เฮอร์คิวลีส)</span>
            </div>
        </div>
        <div class="messier-item">
            <h2>M14</h2>
            <img src="" alt="Messier 14" onerror="this.onerror=null;this.style.display='none'; this.parentNode.querySelector('.no-image').style.display='flex';">
            <div class="no-image" style="display: none;">Add Image for M14</div>
            <p class="common-name"></p>
            <div class="info">
                <span>NGC: 6402</span>
                <span>ประเภท: Globular Cluster</span>
                <span>กลุ่มดาว: Ophiuchus (คนแบกงู)</span>
            </div>
        </div>
        <div class="messier-item">
            <h2>M15</h2>
            <img src="" alt="Messier 15" onerror="this.onerror=null;this.style.display='none'; this.parentNode.querySelector('.no-image').style.display='flex';">
            <div class="no-image" style="display: none;">Add Image for M15</div>
            <p class="common-name"></p>
            <div class="info">
                <span>NGC: 7078</span>
                <span>ประเภท: Globular Cluster</span>
                <span>กลุ่มดาว: Pegasus (ม้าบิน)</span>
            </div>
        </div>
        <div class="messier-item">
            <h2>M16</h2>
            <img src="รูปภาพที่เสร็จเเล้ว/M16 SHO.jpg" alt="Eagle Nebula" onerror="this.onerror=null;this.style.display='none'; this.parentNode.querySelector('.no-image').style.display='flex';">
            <div class="no-image" style="display: none;">Add Image for M16</div>
            <p class="common-name">Eagle Nebula (เนบิวลานกอินทรี)</p>
            <div class="info">
                <span>NGC: 6611</span>
                <span>ประเภท: Open Cluster / Nebula</span>
                <span>กลุ่มดาว: Serpens (งู)</span>
            </div>
        </div>
        <div class="messier-item">
            <h2>M17</h2>
            <img src="รูปภาพที่เสร็จเเล้ว/M17 Omega nebula or swan Nebula SHO style 16 Oct 2025 20.01.jpg" alt="Omega/Swan Nebula" onerror="this.onerror=null;this.style.display='none'; this.parentNode.querySelector('.no-image').style.display='flex';">
            <div class="no-image" style="display: none;">Add Image for M17</div>
            <p class="common-name">Omega/Swan Nebula</p>
            <div class="info">
                <span>NGC: 6618</span>
                <span>ประเภท: Diffuse Nebula</span>
                <span>กลุ่มดาว: Sagittarius (คนยิงธนู)</span>
            </div>
        </div>
        <div class="messier-item">
            <h2>M18</h2>
            <img src="" alt="Messier 18" onerror="this.onerror=null;this.style.display='none'; this.parentNode.querySelector('.no-image').style.display='flex';">
            <div class="no-image" style="display: none;">Add Image for M18</div>
            <p class="common-name"></p>
            <div class="info">
                <span>NGC: 6613</span>
                <span>ประเภท: Open Cluster</span>
                <span>กลุ่มดาว: Sagittarius (คนยิงธนู)</span>
            </div>
        </div>
        <div class="messier-item">
            <h2>M19</h2>
            <img src="" alt="Messier 19" onerror="this.onerror=null;this.style.display='none'; this.parentNode.querySelector('.no-image').style.display='flex';">
            <div class="no-image" style="display: none;">Add Image for M19</div>
            <p class="common-name"></p>
            <div class="info">
                <span>NGC: 6273</span>
                <span>ประเภท: Globular Cluster</span>
                <span>กลุ่มดาว: Ophiuchus (คนแบกงู)</span>
            </div>
        </div>
        <div class="messier-item">
            <h2>M20</h2>
            <img src="รูปภาพที่เสร็จเเล้ว/Trifid Nebula M20 19 Oct 2025 19-12.jpg" alt="Trifid Nebula" onerror="this.onerror=null;this.style.display='none'; this.parentNode.querySelector('.no-image').style.display='flex';">
            <div class="no-image" style="display: none;">Add Image for M20</div>
            <p class="common-name">Trifid Nebula (เนบิวลาสามแฉก)</p>
            <div class="info">
                <span>NGC: 6514</span>
                <span>ประเภท: Diffuse Nebula</span>
                <span>กลุ่มดาว: Sagittarius (คนยิงธนู)</span>
            </div>
        </div>
        <div class="messier-item">
            <h2>M21</h2>
            <img src="" alt="Messier 21" onerror="this.onerror=null;this.style.display='none'; this.parentNode.querySelector('.no-image').style.display='flex';">
            <div class="no-image" style="display: none;">Add Image for M21</div>
            <p class="common-name"></p>
            <div class="info">
                <span>NGC: 6531</span>
                <span>ประเภท: Open Cluster</span>
                <span>กลุ่มดาว: Sagittarius (คนยิงธนู)</span>
            </div>
        </div>
        <div class="messier-item">
            <h2>M22</h2>
            <img src="รูปภาพที่เสร็จเเล้ว/M22.jpg" alt="Sagittarius Cluster" onerror="this.onerror=null;this.style.display='none'; this.parentNode.querySelector('.no-image').style.display='flex';">
            <div class="no-image" style="display: none;">Add Image for M22</div>
            <p class="common-name">Sagittarius Cluster</p>
            <div class="info">
                <span>NGC: 6656</span>
                <span>ประเภท: Globular Cluster</span>
                <span>กลุ่มดาว: Sagittarius (คนยิงธนู)</span>
            </div>
        </div>
        <div class="messier-item">
            <h2>M23</h2>
            <img src="" alt="Messier 23" onerror="this.onerror=null;this.style.display='none'; this.parentNode.querySelector('.no-image').style.display='flex';">
            <div class="no-image" style="display: none;">Add Image for M23</div>
            <p class="common-name"></p>
            <div class="info">
                <span>NGC: 6494</span>
                <span>ประเภท: Open Cluster</span>
                <span>กลุ่มดาว: Sagittarius (คนยิงธนู)</span>
            </div>
        </div>
        <div class="messier-item">
            <h2>M24</h2>
            <img src="" alt="Sagittarius Star Cloud" onerror="this.onerror=null;this.style.display='none'; this.parentNode.querySelector('.no-image').style.display='flex';">
            <div class="no-image" style="display: none;">Add Image for M24</div>
            <p class="common-name">Sagittarius Star Cloud</p>
            <div class="info">
                <span>NGC: (IC 4715)</span>
                <span>ประเภท: Star Cloud</span>
                <span>กลุ่มดาว: Sagittarius (คนยิงธนู)</span>
            </div>
        </div>
        <div class="messier-item">
            <h2>M25</h2>
            <img src="" alt="Messier 25" onerror="this.onerror=null;this.style.display='none'; this.parentNode.querySelector('.no-image').style.display='flex';">
            <div class="no-image" style="display: none;">Add Image for M25</div>
            <p class="common-name"></p>
            <div class="info">
                <span>NGC: (IC 4725)</span>
                <span>ประเภท: Open Cluster</span>
                <span>กลุ่มดาว: Sagittarius (คนยิงธนู)</span>
            </div>
        </div>
        <div class="messier-item">
            <h2>M26</h2>
            <img src="" alt="Messier 26" onerror="this.onerror=null;this.style.display='none'; this.parentNode.querySelector('.no-image').style.display='flex';">
            <div class="no-image" style="display: none;">Add Image for M26</div>
            <p class="common-name"></p>
            <div class="info">
                <span>NGC: 6694</span>
                <span>ประเภท: Open Cluster</span>
                <span>กลุ่มดาว: Scutum (โล่)</span>
            </div>
        </div>
        <div class="messier-item">
            <h2>M27</h2>
            <img src="" alt="Dumbbell Nebula" onerror="this.onerror=null;this.style.display='none'; this.parentNode.querySelector('.no-image').style.display='flex';">
            <div class="no-image" style="display: none;">Add Image for M27</div>
            <p class="common-name">Dumbbell Nebula (เนบิวลาดัมเบล)</p>
            <div class="info">
                <span>NGC: 6853</span>
                <span>ประเภท: Planetary Nebula</span>
                <span>กลุ่มดาว: Vulpecula (สุนัขจิ้งจอก)</span>
            </div>
        </div>
        <div class="messier-item">
            <h2>M28</h2>
            <img src="" alt="Messier 28" onerror="this.onerror=null;this.style.display='none'; this.parentNode.querySelector('.no-image').style.display='flex';">
            <div class="no-image" style="display: none;">Add Image for M28</div>
            <p class="common-name"></p>
            <div class="info">
                <span>NGC: 6626</span>
                <span>ประเภท: Globular Cluster</span>
                <span>กลุ่มดาว: Sagittarius (คนยิงธนู)</span>
            </div>
        </div>
        <div class="messier-item">
            <h2>M29</h2>
            <img src="" alt="Messier 29" onerror="this.onerror=null;this.style.display='none'; this.parentNode.querySelector('.no-image').style.display='flex';">
            <div class="no-image" style="display: none;">Add Image for M29</div>
            <p class="common-name"></p>
            <div class="info">
                <span>NGC: 6913</span>
                <span>ประเภท: Open Cluster</span>
                <span>กลุ่มดาว: Cygnus (หงส์)</span>
            </div>
        </div>
        <div class="messier-item">
            <h2>M30</h2>
            <img src="" alt="Messier 30" onerror="this.onerror=null;this.style.display='none'; this.parentNode.querySelector('.no-image').style.display='flex';">
            <div class="no-image" style="display: none;">Add Image for M30</div>
            <p class="common-name"></p>
            <div class="info">
                <span>NGC: 7099</span>
                <span>ประเภท: Globular Cluster</span>
                <span>กลุ่มดาว: Capricornus (แพะทะเล)</span>
            </div>
        </div>
        <div class="messier-item">
            <h2>M31</h2>
            <img src="รูปภาพที่เสร็จเเล้ว/Messier 31.jpg" alt="Andromeda Galaxy" onerror="this.onerror=null;this.style.display='none'; this.parentNode.querySelector('.no-image').style.display='flex';">
            <div class="no-image" style="display: none;">Add Image for M31</div>
            <p class="common-name">Andromeda Galaxy (กาแล็กซีแอนโดรเมดา)</p>
            <div class="info">
                <span>NGC: 224</span>
                <span>ประเภท: Galaxy</span>
                <span>กลุ่มดาว: Andromeda (แอนโดรเมดา)</span>
            </div>
        </div>
        <div class="messier-item">
            <h2>M32</h2>
            <img src="" alt="Messier 32" onerror="this.onerror=null;this.style.display='none'; this.parentNode.querySelector('.no-image').style.display='flex';">
            <div class="no-image" style="display: none;">Add Image for M32</div>
            <p class="common-name"></p>
            <div class="info">
                <span>NGC: 221</span>
                <span>ประเภท: Galaxy</span>
                <span>กลุ่มดาว: Andromeda (แอนโดรเมดา)</span>
            </div>
        </div>
        <div class="messier-item">
            <h2>M33</h2>
            <img src="" alt="Triangulum Galaxy" onerror="this.onerror=null;this.style.display='none'; this.parentNode.querySelector('.no-image').style.display='flex';">
            <div class="no-image" style="display: none;">Add Image for M33</div>
            <p class="common-name">Triangulum Galaxy (กาแล็กซีสามเหลี่ยม)</p>
            <div class="info">
                <span>NGC: 598</span>
                <span>ประเภท: Galaxy</span>
                <span>กลุ่มดาว: Triangulum (สามเหลี่ยม)</span>
            </div>
        </div>
        <div class="messier-item">
            <h2>M34</h2>
            <img src="" alt="Messier 34" onerror="this.onerror=null;this.style.display='none'; this.parentNode.querySelector('.no-image').style.display='flex';">
            <div class="no-image" style="display: none;">Add Image for M34</div>
            <p class="common-name"></p>
            <div class="info">
                <span>NGC: 1039</span>
                <span>ประเภท: Open Cluster</span>
                <span>กลุ่มดาว: Perseus (เพอร์ซิอุส)</span>
            </div>
        </div>
        <div class="messier-item">
            <h2>M35</h2>
            <img src="" alt="Messier 35" onerror="this.onerror=null;this.style.display='none'; this.parentNode.querySelector('.no-image').style.display='flex';">
            <div class="no-image" style="display: none;">Add Image for M35</div>
            <p class="common-name"></p>
            <div class="info">
                <span>NGC: 2168</span>
                <span>ประเภท: Open Cluster</span>
                <span>กลุ่มดาว: Gemini (คนคู่)</span>
            </div>
        </div>
        <div class="messier-item">
            <h2>M36</h2>
            <img src="" alt="Messier 36" onerror="this.onerror=null;this.style.display='none'; this.parentNode.querySelector('.no-image').style.display='flex';">
            <div class="no-image" style="display: none;">Add Image for M36</div>
            <p class="common-name"></p>
            <div class="info">
                <span>NGC: 1960</span>
                <span>ประเภท: Open Cluster</span>
                <span>กลุ่มดาว: Auriga (สารถี)</span>
            </div>
        </div>
        <div class="messier-item">
            <h2>M37</h2>
            <img src="" alt="Messier 37" onerror="this.onerror=null;this.style.display='none'; this.parentNode.querySelector('.no-image').style.display='flex';">
            <div class="no-image" style="display: none;">Add Image for M37</div>
            <p class="common-name"></p>
            <div class="info">
                <span>NGC: 2099</span>
                <span>ประเภท: Open Cluster</span>
                <span>กลุ่มดาว: Auriga (สารถี)</span>
            </div>
        </div>
        <div class="messier-item">
            <h2>M38</h2>
            <img src="" alt="Messier 38" onerror="this.onerror=null;this.style.display='none'; this.parentNode.querySelector('.no-image').style.display='flex';">
            <div class="no-image" style="display: none;">Add Image for M38</div>
            <p class="common-name"></p>
            <div class="info">
                <span>NGC: 1912</span>
                <span>ประเภท: Open Cluster</span>
                <span>กลุ่มดาว: Auriga (สารถี)</span>
            </div>
        </div>
        <div class="messier-item">
            <h2>M39</h2>
            <img src="" alt="Messier 39" onerror="this.onerror=null;this.style.display='none'; this.parentNode.querySelector('.no-image').style.display='flex';">
            <div class="no-image" style="display: none;">Add Image for M39</div>
            <p class="common-name"></p>
            <div class="info">
                <span>NGC: 7092</span>
                <span>ประเภท: Open Cluster</span>
                <span>กลุ่มดาว: Cygnus (หงส์)</span>
            </div>
        </div>
        <div class="messier-item">
            <h2>M40</h2>
            <img src="" alt="Messier 40" onerror="this.onerror=null;this.style.display='none'; this.parentNode.querySelector('.no-image').style.display='flex';">
            <div class="no-image" style="display: none;">Add Image for M40</div>
            <p class="common-name"></p>
            <div class="info">
                <span>NGC: (WNC 4)</span>
                <span>ประเภท: Double Star</span>
                <span>กลุ่มดาว: Ursa Major (หมีใหญ่)</span>
            </div>
        </div>
        <div class="messier-item">
            <h2>M41</h2>
            <img src="" alt="Messier 41" onerror="this.onerror=null;this.style.display='none'; this.parentNode.querySelector('.no-image').style.display='flex';">
            <div class="no-image" style="display: none;">Add Image for M41</div>
            <p class="common-name"></p>
            <div class="info">
                <span>NGC: 2287</span>
                <span>ประเภท: Open Cluster</span>
                <span>กลุ่มดาว: Canis Major (หมาใหญ่)</span>
            </div>
        </div>
        <div class="messier-item">
            <h2>M42</h2>
            <img src="รูปภาพที่เสร็จเเล้ว/2025-03-28T16.59.28.png" alt="Orion Nebula" onerror="this.onerror=null;this.style.display='none'; this.parentNode.querySelector('.no-image').style.display='flex';">
            <div class="no-image" style="display: none;">Add Image for M42</div>
            <p class="common-name">Orion Nebula (เนบิวลานายพราน)</p>
            <div class="info">
                <span>NGC: 1976</span>
                <span>ประเภท: Diffuse Nebula</span>
                <span>กลุ่มดาว: Orion (นายพราน)</span>
            </div>
        </div>
        <div class="messier-item">
            <h2>M43</h2>
            <img src="" alt="De Mairan's Nebula" onerror="this.onerror=null;this.style.display='none'; this.parentNode.querySelector('.no-image').style.display='flex';">
            <div class="no-image" style="display: none;">Add Image for M43</div>
            <p class="common-name">De Mairan's Nebula</p>
            <div class="info">
                <span>NGC: 1982</span>
                <span>ประเภท: Diffuse Nebula</span>
                <span>กลุ่มดาว: Orion (นายพราน)</span>
            </div>
        </div>
        <div class="messier-item">
            <h2>M44</h2>
            <img src="" alt="Beehive Cluster" onerror="this.onerror=null;this.style.display='none'; this.parentNode.querySelector('.no-image').style.display='flex';">
            <div class="no-image" style="display: none;">Add Image for M44</div>
            <p class="common-name">Beehive Cluster (กระจุกดาวรังผึ้ง)</p>
            <div class="info">
                <span>NGC: 2632</span>
                <span>ประเภท: Open Cluster</span>
                <span>กลุ่มดาว: Cancer (ปู)</span>
            </div>
        </div>
        <div class="messier-item">
            <h2>M45</h2>
            <img src="รูปภาพที่เสร็จเเล้ว/M45 13 Oct 3035 Utah UTC(-6).jpg" alt="Pleiades" onerror="this.onerror=null;this.style.display='none'; this.parentNode.querySelector('.no-image').style.display='flex';">
            <div class="no-image" style="display: none;">Add Image for M45</div>
            <p class="common-name">Pleiades (กระจุกดาวลูกไก่)</p>
            <div class="info">
                <span>NGC: (Pleiades)</span>
                <span>ประเภท: Open Cluster</span>
                <span>กลุ่มดาว: Taurus (วัว)</span>
            </div>
        </div>
        <div class="messier-item">
            <h2>M46</h2>
            <img src="" alt="Messier 46" onerror="this.onerror=null;this.style.display='none'; this.parentNode.querySelector('.no-image').style.display='flex';">
            <div class="no-image" style="display: none;">Add Image for M46</div>
            <p class="common-name"></p>
            <div class="info">
                <span>NGC: 2437</span>
                <span>ประเภท: Open Cluster</span>
                <span>กลุ่มดาว: Puppis (ท้ายเรือ)</span>
            </div>
        </div>
        <div class="messier-item">
            <h2>M47</h2>
            <img src="" alt="Messier 47" onerror="this.onerror=null;this.style.display='none'; this.parentNode.querySelector('.no-image').style.display='flex';">
            <div class="no-image" style="display: none;">Add Image for M47</div>
            <p class="common-name"></p>
            <div class="info">
                <span>NGC: 2422</span>
                <span>ประเภท: Open Cluster</span>
                <span>กลุ่มดาว: Puppis (ท้ายเรือ)</span>
            </div>
        </div>
        <div class="messier-item">
            <h2>M48</h2>
            <img src="" alt="Messier 48" onerror="this.onerror=null;this.style.display='none'; this.parentNode.querySelector('.no-image').style.display='flex';">
            <div class="no-image" style="display: none;">Add Image for M48</div>
            <p class="common-name"></p>
            <div class="info">
                <span>NGC: 2548</span>
                <span>ประเภท: Open Cluster</span>
                <span>กลุ่มดาว: Hydra (งูไฮดรา)</span>
            </div>
        </div>
        <div class="messier-item">
            <h2>M49</h2>
            <img src="" alt="Messier 49" onerror="this.onerror=null;this.style.display='none'; this.parentNode.querySelector('.no-image').style.display='flex';">
            <div class="no-image" style="display: none;">Add Image for M49</div>
            <p class="common-name"></p>
            <div class="info">
                <span>NGC: 4472</span>
                <span>ประเภท: Galaxy</span>
                <span>กลุ่มดาว: Virgo (หญิงสาว)</span>
            </div>
        </div>
        <div class="messier-item">
            <h2>M50</h2>
            <img src="" alt="Messier 50" onerror="this.onerror=null;this.style.display='none'; this.parentNode.querySelector('.no-image').style.display='flex';">
            <div class="no-image" style="display: none;">Add Image for M50</div>
            <p class="common-name"></p>
            <div class="info">
                <span>NGC: 2323</span>
                <span>ประเภท: Open Cluster</span>
                <span>กลุ่มดาว: Monoceros (ยูนิคอร์น)</span>
            </div>
        </div>
        <div class="messier-item">
            <h2>M51</h2>
            <img src="" alt="Whirlpool Galaxy" onerror="this.onerror=null;this.style.display='none'; this.parentNode.querySelector('.no-image').style.display='flex';">
            <div class="no-image" style="display: none;">Add Image for M51</div>
            <p class="common-name">Whirlpool Galaxy (กาแล็กซีน้ำวน)</p>
            <div class="info">
                <span>NGC: 5194</span>
                <span>ประเภท: Galaxy</span>
                <span>กลุ่มดาว: Canes Venatici (หมาล่าเนื้อ)</span>
            </div>
        </div>
        <div class="messier-item">
            <h2>M52</h2>
            <img src="" alt="Messier 52" onerror="this.onerror=null;this.style.display='none'; this.parentNode.querySelector('.no-image').style.display='flex';">
            <div class="no-image" style="display: none;">Add Image for M52</div>
            <p class="common-name"></p>
            <div class="info">
                <span>NGC: 7654</span>
                <span>ประเภท: Open Cluster</span>
                <span>กลุ่มดาว: Cassiopeia (ค้างคาว)</span>
            </div>
        </div>
        <div class="messier-item">
            <h2>M53</h2>
            <img src="" alt="Messier 53" onerror="this.onerror=null;this.style.display='none'; this.parentNode.querySelector('.no-image').style.display='flex';">
            <div class="no-image" style="display: none;">Add Image for M53</div>
            <p class="common-name"></p>
            <div class="info">
                <span>NGC: 5024</span>
                <span>ประเภท: Globular Cluster</span>
                <span>กลุ่มดาว: Coma Berenices (ผมของเบเรนีซ)</span>
            </div>
        </div>
        <div class="messier-item">
            <h2>M54</h2>
            <img src="" alt="Messier 54" onerror="this.onerror=null;this.style.display='none'; this.parentNode.querySelector('.no-image').style.display='flex';">
            <div class="no-image" style="display: none;">Add Image for M54</div>
            <p class="common-name"></p>
            <div class="info">
                <span>NGC: 6715</span>
                <span>ประเภท: Globular Cluster</span>
                <span>กลุ่มดาว: Sagittarius (คนยิงธนู)</span>
            </div>
        </div>
        <div class="messier-item">
            <h2>M55</h2>
            <img src="" alt="Messier 55" onerror="this.onerror=null;this.style.display='none'; this.parentNode.querySelector('.no-image').style.display='flex';">
            <div class="no-image" style="display: none;">Add Image for M55</div>
            <p class="common-name"></p>
            <div class="info">
                <span>NGC: 6809</span>
                <span>ประเภท: Globular Cluster</span>
                <span>กลุ่มดาว: Sagittarius (คนยิงธนู)</span>
            </div>
        </div>
        <div class="messier-item">
            <h2>M56</h2>
            <img src="" alt="Messier 56" onerror="this.onerror=null;this.style.display='none'; this.parentNode.querySelector('.no-image').style.display='flex';">
            <div class="no-image" style="display: none;">Add Image for M56</div>
            <p class="common-name"></p>
            <div class="info">
                <span>NGC: 6779</span>
                <span>ประเภท: Globular Cluster</span>
                <span>กลุ่มดาว: Lyra (พิณ)</span>
            </div>
        </div>
        <div class="messier-item">
            <h2>M57</h2>
            <img src="" alt="Ring Nebula" onerror="this.onerror=null;this.style.display='none'; this.parentNode.querySelector('.no-image').style.display='flex';">
            <div class="no-image" style="display: none;">Add Image for M57</div>
            <p class="common-name">Ring Nebula (เนบิวลาวงแหวน)</p>
            <div class="info">
                <span>NGC: 6720</span>
                <span>ประเภท: Planetary Nebula</span>
                <span>กลุ่มดาว: Lyra (พิณ)</span>
            </div>
        </div>
        <div class="messier-item">
            <h2>M58</h2>
            <img src="" alt="Messier 58" onerror="this.onerror=null;this.style.display='none'; this.parentNode.querySelector('.no-image').style.display='flex';">
            <div class="no-image" style="display: none;">Add Image for M58</div>
            <p class="common-name"></p>
            <div class="info">
                <span>NGC: 4579</span>
                <span>ประเภท: Galaxy</span>
                <span>กลุ่มดาว: Virgo (หญิงสาว)</span>
            </div>
        </div>
        <div class="messier-item">
            <h2>M59</h2>
            <img src="" alt="Messier 59" onerror="this.onerror=null;this.style.display='none'; this.parentNode.querySelector('.no-image').style.display='flex';">
            <div class="no-image" style="display: none;">Add Image for M59</div>
            <p class="common-name"></p>
            <div class="info">
                <span>NGC: 4621</span>
                <span>ประเภท: Galaxy</span>
                <span>กลุ่มดาว: Virgo (หญิงสาว)</span>
            </div>
        </div>
        <div class="messier-item">
            <h2>M60</h2>
            <img src="" alt="Messier 60" onerror="this.onerror=null;this.style.display='none'; this.parentNode.querySelector('.no-image').style.display='flex';">
            <div class="no-image" style="display: none;">Add Image for M60</div>
            <p class="common-name"></p>
            <div class="info">
                <span>NGC: 4649</span>
                <span>ประเภท: Galaxy</span>
                <span>กลุ่มดาว: Virgo (หญิงสาว)</span>
            </div>
        </div>
        <div class="messier-item">
            <h2>M61</h2>
            <img src="" alt="Messier 61" onerror="this.onerror=null;this.style.display='none'; this.parentNode.querySelector('.no-image').style.display='flex';">
            <div class="no-image" style="display: none;">Add Image for M61</div>
            <p class="common-name"></p>
            <div class="info">
                <span>NGC: 4303</span>
                <span>ประเภท: Galaxy</span>
                <span>กลุ่มดาว: Virgo (หญิงสาว)</span>
            </div>
        </div>
        <div class="messier-item">
            <h2>M62</h2>
            <img src="" alt="Messier 62" onerror="this.onerror=null;this.style.display='none'; this.parentNode.querySelector('.no-image').style.display='flex';">
            <div class="no-image" style="display: none;">Add Image for M62</div>
            <p class="common-name"></p>
            <div class="info">
                <span>NGC: 6266</span>
                <span>ประเภท: Globular Cluster</span>
                <span>กลุ่มดาว: Ophiuchus (คนแบกงู)</span>
            </div>
        </div>
        <div class="messier-item">
            <h2>M63</h2>
            <img src="" alt="Sunflower Galaxy" onerror="this.onerror=null;this.style.display='none'; this.parentNode.querySelector('.no-image').style.display='flex';">
            <div class="no-image" style="display: none;">Add Image for M63</div>
            <p class="common-name">Sunflower Galaxy (กาแล็กซีทานตะวัน)</p>
            <div class="info">
                <span>NGC: 5055</span>
                <span>ประเภท: Galaxy</span>
                <span>กลุ่มดาว: Canes Venatici (หมาล่าเนื้อ)</span>
            </div>
        </div>
        <div class="messier-item">
            <h2>M64</h2>
            <img src="" alt="Black-Eye Galaxy" onerror="this.onerror=null;this.style.display='none'; this.parentNode.querySelector('.no-image').style.display='flex';">
            <div class="no-image" style="display: none;">Add Image for M64</div>
            <p class="common-name">Black-Eye Galaxy</p>
            <div class="info">
                <span>NGC: 4826</span>
                <span>ประเภท: Galaxy</span>
                <span>กลุ่มดาว: Coma Berenices (ผมของเบเรนีซ)</span>
            </div>
        </div>
        <div class="messier-item">
            <h2>M65</h2>
            <img src="" alt="Messier 65" onerror="this.onerror=null;this.style.display='none'; this.parentNode.querySelector('.no-image').style.display='flex';">
            <div class="no-image" style="display: none;">Add Image for M65</div>
            <p class="common-name"></p>
            <div class="info">
                <span>NGC: 3623</span>
                <span>ประเภท: Galaxy</span>
                <span>กลุ่มดาว: Leo (สิงโต)</span>
            </div>
        </div>
        <div class="messier-item">
            <h2>M66</h2>
            <img src="" alt="Messier 66" onerror="this.onerror=null;this.style.display='none'; this.parentNode.querySelector('.no-image').style.display='flex';">
            <div class="no-image" style="display: none;">Add Image for M66</div>
            <p class="common-name"></p>
            <div class="info">
                <span>NGC: 3627</span>
                <span>ประเภท: Galaxy</span>
                <span>กลุ่มดาว: Leo (สิงโต)</span>
            </div>
        </div>
        <div class="messier-item">
            <h2>M67</h2>
            <img src="" alt="Messier 67" onerror="this.onerror=null;this.style.display='none'; this.parentNode.querySelector('.no-image').style.display='flex';">
            <div class="no-image" style="display: none;">Add Image for M67</div>
            <p class="common-name"></p>
            <div class="info">
                <span>NGC: 2682</span>
                <span>ประเภท: Open Cluster</span>
                <span>กลุ่มดาว: Cancer (ปู)</span>
            </div>
        </div>
        <div class="messier-item">
            <h2>M68</h2>
            <img src="" alt="Messier 68" onerror="this.onerror=null;this.style.display='none'; this.parentNode.querySelector('.no-image').style.display='flex';">
            <div class="no-image" style="display: none;">Add Image for M68</div>
            <p class="common-name"></p>
            <div class="info">
                <span>NGC: 4590</span>
                <span>ประเภท: Globular Cluster</span>
                <span>กลุ่มดาว: Hydra (งูไฮดรา)</span>
            </div>
        </div>
        <div class="messier-item">
            <h2>M69</h2>
            <img src="" alt="Messier 69" onerror="this.onerror=null;this.style.display='none'; this.parentNode.querySelector('.no-image').style.display='flex';">
            <div class="no-image" style="display: none;">Add Image for M69</div>
            <p class="common-name"></p>
            <div class="info">
                <span>NGC: 6637</span>
                <span>ประเภท: Globular Cluster</span>
                <span>กลุ่มดาว: Sagittarius (คนยิงธนู)</span>
            </div>
        </div>
        <div class="messier-item">
            <h2>M70</h2>
            <img src="" alt="Messier 70" onerror="this.onerror=null;this.style.display='none'; this.parentNode.querySelector('.no-image').style.display='flex';">
            <div class="no-image" style="display: none;">Add Image for M70</div>
            <p class="common-name"></p>
            <div class="info">
                <span>NGC: 6681</span>
                <span>ประเภท: Globular Cluster</span>
                <span>กลุ่มดาว: Sagittarius (คนยิงธนู)</span>
            </div>
        </div>
        <div class="messier-item">
            <h2>M71</h2>
            <img src="" alt="Messier 71" onerror="this.onerror=null;this.style.display='none'; this.parentNode.querySelector('.no-image').style.display='flex';">
            <div class="no-image" style="display: none;">Add Image for M71</div>
            <p class="common-name"></p>
            <div class="info">
                <span>NGC: 6838</span>
                <span>ประเภท: Globular Cluster</span>
                <span>กลุ่มดาว: Sagitta (ลูกศร)</span>
            </div>
        </div>
        <div class="messier-item">
            <h2>M72</h2>
            <img src="" alt="Messier 72" onerror="this.onerror=null;this.style.display='none'; this.parentNode.querySelector('.no-image').style.display='flex';">
            <div class="no-image" style="display: none;">Add Image for M72</div>
            <p class="common-name"></p>
            <div class="info">
                <span>NGC: 6981</span>
                <span>ประเภท: Globular Cluster</span>
                <span>กลุ่มดาว: Aquarius (คนแบกหม้อน้ำ)</span>
            </div>
        </div>
        <div class="messier-item">
            <h2>M73</h2>
            <img src="" alt="Messier 73" onerror="this.onerror=null;this.style.display='none'; this.parentNode.querySelector('.no-image').style.display='flex';">
            <div class="no-image" style="display: none;">Add Image for M73</div>
            <p class="common-name"></p>
            <div class="info">
                <span>NGC: 6994</span>
                <span>ประเภท: Asterism</span>
                <span>กลุ่มดาว: Aquarius (คนแบกหม้อน้ำ)</span>
            </div>
        </div>
        <div class="messier-item">
            <h2>M74</h2>
            <img src="รูปภาพที่เสร็จเเล้ว/M74 13 Oct 2025 Utah UTC-6,2.jpg" alt="Phantom Galaxy" onerror="this.onerror=null;this.style.display='none'; this.parentNode.querySelector('.no-image').style.display='flex';">
            <div class="no-image" style="display: none;">Add Image for M74</div>
            <p class="common-name">Phantom Galaxy</p>
            <div class="info">
                <span>NGC: 628</span>
                <span>ประเภท: Galaxy</span>
                <span>กลุ่มดาว: Pisces (ปลา)</span>
            </div>
        </div>
        <div class="messier-item">
            <h2>M75</h2>
            <img src="" alt="Messier 75" onerror="this.onerror=null;this.style.display='none'; this.parentNode.querySelector('.no-image').style.display='flex';">
            <div class="no-image" style="display: none;">Add Image for M75</div>
            <p class="common-name"></p>
            <div class="info">
                <span>NGC: 6864</span>
                <span>ประเภท: Globular Cluster</span>
                <span>กลุ่มดาว: Sagittarius (คนยิงธนู)</span>
            </div>
        </div>
        <div class="messier-item">
            <h2>M76</h2>
            <img src="" alt="Little Dumbbell Nebula" onerror="this.onerror=null;this.style.display='none'; this.parentNode.querySelector('.no-image').style.display='flex';">
            <div class="no-image" style="display: none;">Add Image for M76</div>
            <p class="common-name">Little Dumbbell Nebula</p>
            <div class="info">
                <span>NGC: 650/651</span>
                <span>ประเภท: Planetary Nebula</span>
                <span>กลุ่มดาว: Perseus (เพอร์ซิอุส)</span>
            </div>
        </div>
        <div class="messier-item">
            <h2>M77</h2>
            <img src="" alt="Messier 77" onerror="this.onerror=null;this.style.display='none'; this.parentNode.querySelector('.no-image').style.display='flex';">
            <div class="no-image" style="display: none;">Add Image for M77</div>
            <p class="common-name"></p>
            <div class="info">
                <span>NGC: 1068</span>
                <span>ประเภท: Galaxy</span>
                <span>กลุ่มดาว: Cetus (วาฬ)</span>
            </div>
        </div>
        <div class="messier-item">
            <h2>M78</h2>
            <img src="รูปภาพที่เสร็จเเล้ว/M78.fits.jpg" alt="Messier 78" onerror="this.onerror=null;this.style.display='none'; this.parentNode.querySelector('.no-image').style.display='flex';">
            <div class="no-image" style="display: none;">Add Image for M78</div>
            <p class="common-name"></p>
            <div class="info">
                <span>NGC: 2068</span>
                <span>ประเภท: Diffuse Nebula</span>
                <span>กลุ่มดาว: Orion (นายพราน)</span>
            </div>
        </div>
        <div class="messier-item">
            <h2>M79</h2>
            <img src="" alt="Messier 79" onerror="this.onerror=null;this.style.display='none'; this.parentNode.querySelector('.no-image').style.display='flex';">
            <div class="no-image" style="display: none;">Add Image for M79</div>
            <p class="common-name"></p>
            <div class="info">
                <span>NGC: 1904</span>
                <span>ประเภท: Globular Cluster</span>
                <span>กลุ่มดาว: Lepus (กระต่ายป่า)</span>
            </div>
        </div>
        <div class="messier-item">
            <h2>M80</h2>
            <img src="" alt="Messier 80" onerror="this.onerror=null;this.style.display='none'; this.parentNode.querySelector('.no-image').style.display='flex';">
            <div class="no-image" style="display: none;">Add Image for M80</div>
            <p class="common-name"></p>
            <div class="info">
                <span>NGC: 6093</span>
                <span>ประเภท: Globular Cluster</span>
                <span>กลุ่มดาว: Scorpius (แมงป่อง)</span>
            </div>
        </div>
        <div class="messier-item">
            <h2>M81</h2>
            <img src="" alt="Bode's Galaxy" onerror="this.onerror=null;this.style.display='none'; this.parentNode.querySelector('.no-image').style.display='flex';">
            <div class="no-image" style="display: none;">Add Image for M81</div>
            <p class="common-name">Bode's Galaxy</p>
            <div class="info">
                <span>NGC: 3031</span>
                <span>ประเภท: Galaxy</span>
                <span>กลุ่มดาว: Ursa Major (หมีใหญ่)</span>
            </div>
        </div>
        <div class="messier-item">
            <h2>M82</h2>
            <img src="" alt="Cigar Galaxy" onerror="this.onerror=null;this.style.display='none'; this.parentNode.querySelector('.no-image').style.display='flex';">
            <div class="no-image" style="display: none;">Add Image for M82</div>
            <p class="common-name">Cigar Galaxy (กาแล็กซีซิการ์)</p>
            <div class="info">
                <span>NGC: 3034</span>
                <span>ประเภท: Galaxy</span>
                <span>กลุ่มดาว: Ursa Major (หมีใหญ่)</span>
            </div>
        </div>
        <div class="messier-item">
            <h2>M83</h2>
            <img src="" alt="Southern Pinwheel Galaxy" onerror="this.onerror=null;this.style.display='none'; this.parentNode.querySelector('.no-image').style.display='flex';">
            <div class="no-image" style="display: none;">Add Image for M83</div>
            <p class="common-name">Southern Pinwheel Galaxy</p>
            <div class="info">
                <span>NGC: 5236</span>
                <span>ประเภท: Galaxy</span>
                <span>กลุ่มดาว: Hydra (งูไฮดรา)</span>
            </div>
        </div>
        <div class="messier-item">
            <h2>M84</h2>
            <img src="" alt="Messier 84" onerror="this.onerror=null;this.style.display='none'; this.parentNode.querySelector('.no-image').style.display='flex';">
            <div class="no-image" style="display: none;">Add Image for M84</div>
            <p class="common-name"></p>
            <div class="info">
                <span>NGC: 4374</span>
                <span>ประเภท: Galaxy</span>
                <span>กลุ่มดาว: Virgo (หญิงสาว)</span>
            </div>
        </div>
        <div class="messier-item">
            <h2>M85</h2>
            <img src="" alt="Messier 85" onerror="this.onerror=null;this.style.display='none'; this.parentNode.querySelector('.no-image').style.display='flex';">
            <div class="no-image" style="display: none;">Add Image for M85</div>
            <p class="common-name"></p>
            <div class="info">
                <span>NGC: 4382</span>
                <span>ประเภท: Galaxy</span>
                <span>กลุ่มดาว: Coma Berenices (ผมของเบเรนีซ)</span>
            </div>
        </div>
        <div class="messier-item">
            <h2>M86</h2>
            <img src="" alt="Messier 86" onerror="this.onerror=null;this.style.display='none'; this.parentNode.querySelector('.no-image').style.display='flex';">
            <div class="no-image" style="display: none;">Add Image for M86</div>
            <p class="common-name"></p>
            <div class="info">
                <span>NGC: 4406</span>
                <span>ประเภท: Galaxy</span>
                <span>กลุ่มดาว: Virgo (หญิงสาว)</span>
            </div>
        </div>
        <div class="messier-item">
            <h2>M87</h2>
            <img src="" alt="Messier 87" onerror="this.onerror=null;this.style.display='none'; this.parentNode.querySelector('.no-image').style.display='flex';">
            <div class="no-image" style="display: none;">Add Image for M87</div>
            <p class="common-name"></p>
            <div class="info">
                <span>NGC: 4486</span>
                <span>ประเภท: Galaxy</span>
                <span>กลุ่มดาว: Virgo (หญิงสาว)</span>
            </div>
        </div>
        <div class="messier-item">
            <h2>M88</h2>
            <img src="" alt="Messier 88" onerror="this.onerror=null;this.style.display='none'; this.parentNode.querySelector('.no-image').style.display='flex';">
            <div class="no-image" style="display: none;">Add Image for M88</div>
            <p class="common-name"></p>
            <div class="info">
                <span>NGC: 4501</span>
                <span>ประเภท: Galaxy</span>
                <span>กลุ่มดาว: Coma Berenices (ผมของเบเรนีซ)</span>
            </div>
        </div>
        <div class="messier-item">
            <h2>M89</h2>
            <img src="" alt="Messier 89" onerror="this.onerror=null;this.style.display='none'; this.parentNode.querySelector('.no-image').style.display='flex';">
            <div class="no-image" style="display: none;">Add Image for M89</div>
            <p class="common-name"></p>
            <div class="info">
                <span>NGC: 4552</span>
                <span>ประเภท: Galaxy</span>
                <span>กลุ่มดาว: Virgo (หญิงสาว)</span>
            </div>
        </div>
        <div class="messier-item">
            <h2>M90</h2>
            <img src="" alt="Messier 90" onerror="this.onerror=null;this.style.display='none'; this.parentNode.querySelector('.no-image').style.display='flex';">
            <div class="no-image" style="display: none;">Add Image for M90</div>
            <p class="common-name"></p>
            <div class="info">
                <span>NGC: 4569</span>
                <span>ประเภท: Galaxy</span>
                <span>กลุ่มดาว: Virgo (หญิงสาว)</span>
            </div>
        </div>
        <div class="messier-item">
            <h2>M91</h2>
            <img src="" alt="Messier 91" onerror="this.onerror=null;this.style.display='none'; this.parentNode.querySelector('.no-image').style.display='flex';">
            <div class="no-image" style="display: none;">Add Image for M91</div>
            <p class="common-name"></p>
            <div class="info">
                <span>NGC: 4548</span>
                <span>ประเภท: Galaxy</span>
                <span>กลุ่มดาว: Coma Berenices (ผมของเบเรนีซ)</span>
            </div>
        </div>
        <div class="messier-item">
            <h2>M92</h2>
            <img src="" alt="Messier 92" onerror="this.onerror=null;this.style.display='none'; this.parentNode.querySelector('.no-image').style.display='flex';">
            <div class="no-image" style="display: none;">Add Image for M92</div>
            <p class="common-name"></p>
            <div class="info">
                <span>NGC: 6341</span>
                <span>ประเภท: Globular Cluster</span>
                <span>กลุ่มดาว: Hercules (เฮอร์คิวลีส)</span>
            </div>
        </div>
        <div class="messier-item">
            <h2>M93</h2>
            <img src="" alt="Messier 93" onerror="this.onerror=null;this.style.display='none'; this.parentNode.querySelector('.no-image').style.display='flex';">
            <div class="no-image" style="display: none;">Add Image for M93</div>
            <p class="common-name"></p>
            <div class="info">
                <span>NGC: 2447</span>
                <span>ประเภท: Open Cluster</span>
                <span>กลุ่มดาว: Puppis (ท้ายเรือ)</span>
            </div>
        </div>
        <div class="messier-item">
            <h2>M94</h2>
            <img src="" alt="Messier 94" onerror="this.onerror=null;this.style.display='none'; this.parentNode.querySelector('.no-image').style.display='flex';">
            <div class="no-image" style="display: none;">Add Image for M94</div>
            <p class="common-name"></p>
            <div class="info">
                <span>NGC: 4736</span>
                <span>ประเภท: Galaxy</span>
                <span>กลุ่มดาว: Canes Venatici (หมาล่าเนื้อ)</span>
            </div>
        </div>
        <div class="messier-item">
            <h2>M95</h2>
            <img src="" alt="Messier 95" onerror="this.onerror=null;this.style.display='none'; this.parentNode.querySelector('.no-image').style.display='flex';">
            <div class="no-image" style="display: none;">Add Image for M95</div>
            <p class="common-name"></p>
            <div class="info">
                <span>NGC: 3351</span>
                <span>ประเภท: Galaxy</span>
                <span>กลุ่มดาว: Leo (สิงโต)</span>
            </div>
        </div>
        <div class="messier-item">
            <h2>M96</h2>
            <img src="" alt="Messier 96" onerror="this.onerror=null;this.style.display='none'; this.parentNode.querySelector('.no-image').style.display='flex';">
            <div class="no-image" style="display: none;">Add Image for M96</div>
            <p class="common-name"></p>
            <div class="info">
                <span>NGC: 3368</span>
                <span>ประเภท: Galaxy</span>
                <span>กลุ่มดาว: Leo (สิงโต)</span>
            </div>
        </div>
        <div class="messier-item">
            <h2>M97</h2>
            <img src="" alt="Owl Nebula" onerror="this.onerror=null;this.style.display='none'; this.parentNode.querySelector('.no-image').style.display='flex';">
            <div class="no-image" style="display: none;">Add Image for M97</div>
            <p class="common-name">Owl Nebula (เนบิวลานกฮูก)</p>
            <div class="info">
                <span>NGC: 3587</span>
                <span>ประเภท: Planetary Nebula</span>
                <span>กลุ่มดาว: Ursa Major (หมีใหญ่)</span>
            </div>
        </div>
        <div class="messier-item">
            <h2>M98</h2>
            <img src="" alt="Messier 98" onerror="this.onerror=null;this.style.display='none'; this.parentNode.querySelector('.no-image').style.display='flex';">
            <div class="no-image" style="display: none;">Add Image for M98</div>
            <p class="common-name"></p>
            <div class="info">
                <span>NGC: 4192</span>
                <span>ประเภท: Galaxy</span>
                <span>กลุ่มดาว: Coma Berenices (ผมของเบเรนีซ)</span>
            </div>
        </div>
        <div class="messier-item">
            <h2>M99</h2>
            <img src="" alt="Messier 99" onerror="this.onerror=null;this.style.display='none'; this.parentNode.querySelector('.no-image').style.display='flex';">
            <div class="no-image" style="display: none;">Add Image for M99</div>
            <p class="common-name"></p>
            <div class="info">
                <span>NGC: 4254</span>
                <span>ประเภท: Galaxy</span>
                <span>กลุ่มดาว: Coma Berenices (ผมของเบเรนีซ)</span>
            </div>
        </div>
        <div class="messier-item">
            <h2>M100</h2>
            <img src="" alt="Messier 100" onerror="this.onerror=null;this.style.display='none'; this.parentNode.querySelector('.no-image').style.display='flex';">
            <div class="no-image" style="display: none;">Add Image for M100</div>
            <p class="common-name"></p>
            <div class="info">
                <span>NGC: 4321</span>
                <span>ประเภท: Galaxy</span>
                <span>กลุ่มดาว: Coma Berenices (ผมของเบเรนีซ)</span>
            </div>
        </div>
        <div class="messier-item">
            <h2>M101</h2>
            <img src="" alt="Pinwheel Galaxy" onerror="this.onerror=null;this.style.display='none'; this.parentNode.querySelector('.no-image').style.display='flex';">
            <div class="no-image" style="display: none;">Add Image for M101</div>
            <p class="common-name">Pinwheel Galaxy (กาแล็กซีกังหัน)</p>
            <div class="info">
                <span>NGC: 5457</span>
                <span>ประเภท: Galaxy</span>
                <span>กลุ่มดาว: Ursa Major (หมีใหญ่)</span>
            </div>
        </div>
        <div class="messier-item">
            <h2>M102</h2>
            <img src="" alt="Spindle Galaxy" onerror="this.onerror=null;this.style.display='none'; this.parentNode.querySelector('.no-image').style.display='flex';">
            <div class="no-image" style="display: none;">Add Image for M102</div>
            <p class="common-name">Spindle Galaxy</p>
            <div class="info">
                <span>NGC: 5866</span>
                <span>ประเภท: Galaxy</span>
                <span>กลุ่มดาว: Draco (มังกร)</span>
            </div>
        </div>
        <div class="messier-item">
            <h2>M103</h2>
            <img src="" alt="Messier 103" onerror="this.onerror=null;this.style.display='none'; this.parentNode.querySelector('.no-image').style.display='flex';">
            <div class="no-image" style="display: none;">Add Image for M103</div>
            <p class="common-name"></p>
            <div class="info">
                <span>NGC: 581</span>
                <span>ประเภท: Open Cluster</span>
                <span>กลุ่มดาว: Cassiopeia (ค้างคาว)</span>
            </div>
        </div>
        <div class="messier-item">
            <h2>M104</h2>
            <img src="" alt="Sombrero Galaxy" onerror="this.onerror=null;this.style.display='none'; this.parentNode.querySelector('.no-image').style.display='flex';">
            <div class="no-image" style="display: none;">Add Image for M104</div>
            <p class="common-name">Sombrero Galaxy (กาแล็กซีสมเบรโร)</p>
            <div class="info">
                <span>NGC: 4594</span>
                <span>ประเภท: Galaxy</span>
                <span>กลุ่มดาว: Virgo (หญิงสาว)</span>
            </div>
        </div>
        <div class="messier-item">
            <h2>M105</h2>
            <img src="" alt="Messier 105" onerror="this.onerror=null;this.style.display='none'; this.parentNode.querySelector('.no-image').style.display='flex';">
            <div class="no-image" style="display: none;">Add Image for M105</div>
            <p class="common-name"></p>
            <div class="info">
                <span>NGC: 3379</span>
                <span>ประเภท: Galaxy</span>
                <span>กลุ่มดาว: Leo (สิงโต)</span>
            </div>
        </div>
        <div class="messier-item">
            <h2>M106</h2>
            <img src="" alt="Messier 106" onerror="this.onerror=null;this.style.display='none'; this.parentNode.querySelector('.no-image').style.display='flex';">
            <div class="no-image" style="display: none;">Add Image for M106</div>
            <p class="common-name"></p>
            <div class="info">
                <span>NGC: 4258</span>
                <span>ประเภท: Galaxy</span>
                <span>กลุ่มดาว: Canes Venatici (หมาล่าเนื้อ)</span>
            </div>
        </div>
        <div class="messier-item">
            <h2>M107</h2>
            <img src="" alt="Messier 107" onerror="this.onerror=null;this.style.display='none'; this.parentNode.querySelector('.no-image').style.display='flex';">
            <div class="no-image" style="display: none;">Add Image for M107</div>
            <p class="common-name"></p>
            <div class="info">
                <span>NGC: 6171</span>
                <span>ประเภท: Globular Cluster</span>
                <span>กลุ่มดาว: Ophiuchus (คนแบกงู)</span>
            </div>
        </div>
        <div class="messier-item">
            <h2>M108</h2>
            <img src="" alt="Messier 108" onerror="this.onerror=null;this.style.display='none'; this.parentNode.querySelector('.no-image').style.display='flex';">
            <div class="no-image" style="display: none;">Add Image for M108</div>
            <p class="common-name"></p>
            <div class="info">
                <span>NGC: 3556</span>
                <span>ประเภท: Galaxy</span>
                <span>กลุ่มดาว: Ursa Major (หมีใหญ่)</span>
            </div>
        </div>
        <div class="messier-item">
            <h2>M109</h2>
            <img src="" alt="Messier 109" onerror="this.onerror=null;this.style.display='none'; this.parentNode.querySelector('.no-image').style.display='flex';">
            <div class="no-image" style="display: none;">Add Image for M109</div>
            <p class="common-name"></p>
            <div class="info">
                <span>NGC: 3992</span>
                <span>ประเภท: Galaxy</span>
                <span>กลุ่มดาว: Ursa Major (หมีใหญ่)</span>
            </div>
        </div>
        <div class="messier-item">
            <h2>M110</h2>
            <img src="" alt="Messier 110" onerror="this.onerror=null;this.style.display='none'; this.parentNode.querySelector('.no-image').style.display='flex';">
            <div class="no-image" style="display: none;">Add Image for M110</div>
            <p class="common-name"></p>
            <div class="info">
                <span>NGC: 205</span>
                <span>ประเภท: Galaxy</span>
                <span>กลุ่มดาว: Andromeda (แอนโดรเมดา)</span>
            </div>
        </div>
    </div> <div id="lightboxOverlay" class="lightbox-overlay">
        <span class="lightbox-close">&times;</span>
        <img id="lightbox-image" src="" alt="ภาพขยาย">
    </div>
    <script>
        document.addEventListener('DOMContentLoaded', () => {  
            const lightboxOverlay = document.getElementById('lightboxOverlay');
            const lightboxImage = document.getElementById('lightbox-image');
            const closeButton = document.querySelector('.lightbox-close');
            const gridImages = document.querySelectorAll('.messier-item img');
            gridImages.forEach(image => {
                image.addEventListener('click', () => {
                    if (image.src && image.src !== window.location.href) { 
                        lightboxImage.src = image.src; 
                        lightboxOverlay.classList.add('lightbox-active'); 
                    }
                });
            });
            function closeLightbox() {
                lightboxOverlay.classList.remove('lightbox-active'); 
                lightboxImage.src = ""; 
            }
            closeButton.addEventListener('click', closeLightbox);
            lightboxOverlay.addEventListener('click', (event) => {
                if (event.target === lightboxOverlay) {
                    closeLightbox();
                }
            });
        });
    </script>

</body>
</html>
