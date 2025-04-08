1. Unduh Model dari Thangs.com
Buka Thangs.com.
Cari dan unduh model 3D yang kamu inginkan.
Pilih format .glb atau .gltf agar kompatibel dengan Babylon.js.
2. Buat Proyek Babylon.js
Kamu bisa menggunakan HTML sederhana untuk memuat model. Berikut langkah-langkahnya:

a) Tambahkan Babylon.js ke dalam HTML
Buat file index.html dan tambahkan kode berikut:

html
Copy
Edit
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Thangs Model in Babylon.js</title>
    <script src="https://cdn.babylonjs.com/babylon.js"></script>
    <script src="https://cdn.babylonjs.com/loaders/babylonjs.loaders.min.js"></script>
</head>
<body>
    <canvas id="renderCanvas"></canvas>

    <script>
        // Inisialisasi Babylon.js
        const canvas = document.getElementById("renderCanvas");
        const engine = new BABYLON.Engine(canvas, true);

        // Buat scene
        const createScene = function () {
            const scene = new BABYLON.Scene(engine);

            // Tambahkan kamera
            const camera = new BABYLON.ArcRotateCamera("camera", Math.PI / 2, Math.PI / 2, 5, BABYLON.Vector3.Zero(), scene);
            camera.attachControl(canvas, true);

            // Tambahkan pencahayaan
            const light = new BABYLON.HemisphericLight("light", new BABYLON.Vector3(0, 1, 0), scene);
            light.intensity = 1.0;

            // Load model dari folder lokal
            BABYLON.SceneLoader.Append("./", "model.glb", scene, function (scene) {
                console.log("Model berhasil dimuat!");
            });

            return scene;
        };

        const scene = createScene();
        engine.runRenderLoop(() => scene.render());

        // Resize handler
        window.addEventListener("resize", () => engine.resize());
    </script>
</body>
</html>
3. Letakkan Model di Folder Proyek
Simpan file index.html di dalam folder proyek.
Pastikan model yang diunduh (model.glb) ada di folder yang sama.
4. Jalankan Proyek
Untuk melihat hasilnya, jalankan proyek menggunakan server lokal:

Jika menggunakan Python (versi 3)

sh
Copy
Edit
python -m http.server 8000
Lalu buka di browser: http://localhost:8000

Jika menggunakan Node.js (dengan package http-server)

sh
Copy
Edit
npx http-server
Kemudian buka di browser.

Tambahan
Jika model terlalu besar atau tidak muncul:

Coba ganti posisi kamera (ArcRotateCamera).
Gunakan SceneLoader.ImportMesh() jika hanya ingin memuat bagian tertentu dari model.
Kalau ada pertanyaan lebih lanjut, tanyakan saja! 🚀
