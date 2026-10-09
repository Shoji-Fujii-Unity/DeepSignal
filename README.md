# DEEP SIGNAL / ディープシグナル

対応言語：日本語 / English / 简体中文 / 한국어 / Español

DEEP SIGNAL は、Three.js で制作した Web 3D ソナー潜行ホラーゲームです。
プレイヤーは深海探査機を操作し、視界ゼロの海溝へ潜ります。
画面には通常何も表示されず、ソナーパルスが当たった地形が一瞬だけ可視化されます。
生物は音源に反応するため、静かに潜航することが安全なルートにつながります。

この README.md は対応言語で書かれた説明ファイルです。
インストール方法、操作方法、保存仕様、デザイン方針、技術仕様を記載しています。

---

## 日本語

### 概要

DEEP SIGNAL は「視界ゼロ。音だけが、地形になる。」というコンセプトのソナー潜行ホラーゲームです。
プレイヤーは深海探査機を操作し、深度 3200m を目指します。

主な特徴：

- 視界ゼロの 3D 深海環境
- 距離マスクシェーダによるソナー表示
- 音に反応する生物 AI
- 3Dオーディオ
- スマホは横長画面で動作
- PC ではマウスドラッグまたはキーボードで操作
- 多言語対応
- ローカルセーブデータ保存
- 想定プレイ時間 8〜12 分

### 実行方法

ゲームは単一の HTML ファイルとして動作する想定です。

1. ゲーム HTML ファイルをローカルに保存する。
2. ブラウザでその HTML ファイルを開く。
3. メニューから言語を選択する。
4. 「潜水開始」を押して開始する。
5. スマホの場合は端末を横向きにする。

外部音声ファイルは不要です。
音声はブラウザの WebAudio API で動的に生成されます。

### 操作

スマホ：

- 画面をドラッグして探査機を移動します。
- 横方向ドラッグは左右移動です。
- 縦方向ドラッグは上下移動です。
- 右下の PULSE ボタンでソナーを放ちます。

PC：

- マウスドラッグで探査機を移動できます。
- キーボード操作も可能です。
- 方向キー W A S D で移動。
- スペースキーで PULSE。

### 遊び方の基本

- 目標深度は 3200m です。
- 画面は基本的に暗闇です。
- ソナーを打つと、波が当たった地形が一瞬だけ描画されます。
- 地形の形状から進路を読みます。
- 岩や壁に接触すると船体が損傷します。
- 生物は音に反応して接近します。
- 移動速度とソナー使用量が増えるほど騒音が高まります。
- 騒音が高いほど生物に気づかれやすくなります。
- 静かに進むほど安全です。

### 保存データ

セーブデータはブラウザの localStorage に保存されます。

保存項目：

- depth：到達済み深度
- log：探索ログ
- lang：選択中の言語

ゲームを途中でやめても、メニューから「続きを開始」を選択できます。
言語設定も保存されます。

### 対応言語

このゲームは以下の言語に対応しています。

- 日本語：ja
- English：en
- 简体中文：zh
- 한국어：ko
- Español：es

言語設定はメニューから変更できます。
変更後、UI 文字列が再描画され、localStorage に保存されます。

### 技術仕様

使用技術：

- Three.js
- WebGL
- GLSL Shader
- WebAudio API
- localStorage

グラフィック方針：

- 地形は一本の隧道として構成
- 岩は InstancedMesh で表示
- 生物は少数メッシュで構成
- 距離マスクシェーダでソナー波面のみ描画
- 描画予算は概ね 50 calls / 90k tris を目安とする

UI：

- 深度
- 船体耐久
- 騒音
- 経過時間
- 探索ログ
- 言語選択
- 音声 ON / OFF

---

## English

### Overview

DEEP SIGNAL is a Web-based 3D sonar stealth horror game built with Three.js.
The player controls a deep-sea probe descending into a zero-visibility trench.
The screen is normally dark. Terrain appears only when a sonar pulse reaches it.
Creatures react to sound, so silent navigation is the safest route.

Main features:

- Zero-visibility 3D deep-sea environment
- Distance-mask sonar shader
- Sound-reactive creature AI
- 3D audio
- Landscape layout on mobile
- Mouse and keyboard controls on PC
- Multilingual UI
- Local save data
- Expected play time: 8 to 12 minutes

### How to Run

The game is intended to run as a single HTML file.

1. Save the game HTML file locally.
2. Open the HTML file in a browser.
3. Select a language from the menu.
4. Start the dive.
5. On mobile, rotate the device to landscape orientation.

No external audio files are required.
All sounds are generated dynamically with the WebAudio API.

### Controls

Mobile:

- Drag the screen to move the probe.
- Horizontal drag moves left and right.
- Vertical drag moves up and down.
- Use the PULSE button to emit sonar.

PC:

- Drag with the mouse to move the probe.
- Keyboard controls are also supported.
- Arrow keys or WASD move the probe.
- Space emits a sonar pulse.

### Gameplay

- Target depth is 3200 meters.
- The screen is mostly darkness.
- Sonar reveals nearby terrain for a brief moment.
- Read terrain from the returning sound wave.
- Collisions with walls and rocks damage the hull.
- Creatures react to sound and approach loud sources.
- Movement and sonar use increase noise.
- Higher noise attracts creatures.
- Moving quietly is safer.

### Save Data

Save data is stored in browser localStorage.

Saved fields:

- depth: reached depth
- log: exploration log
- lang: selected language

Progress can be resumed from the Continue option.
Language settings are also saved.

### Supported Languages

This game supports:

- Japanese: ja
- English: en
- Simplified Chinese: zh
- Korean: ko
- Spanish: es

Language can be changed from the menu.
After changing, UI strings are redrawn and the setting is saved to localStorage.

### Technical Notes

Technologies:

- Three.js
- WebGL
- GLSL shader
- WebAudio API
- localStorage

Graphics policy:

- The environment is one procedural tunnel.
- Rocks are drawn using InstancedMesh.
- Creatures are built from a small number of meshes.
- A distance-mask shader draws only the sonar wavefront.
- Render budget targets roughly 50 draw calls and 90k triangles.

UI:

- Depth
- Hull integrity
- Noise level
- Elapsed time
- Exploration log
- Language selector
- Audio toggle

---

## 简体中文

### 概述

DEEP SIGNAL 是一个使用 Three.js 制作的网页 3D 声呐潜行恐怖游戏。
玩家操作深海探测器，在零可见度的海沟中下潜。
画面通常完全黑暗，只有声呐脉冲照射到的地形会短暂显示。
生物会响应声音，因此保持安静是最安全的路线。

主要特性：

- 零可见度的 3D 深海环境
- 基于距离遮罩的声呐着色器
- 会响应声音的生物 AI
- 3D 音频
- 手机端横屏显示
- PC 端支持鼠标和键盘操作
- 多语言界面
- 本地存档
- 预期游玩时间 8 至 12 分钟

### 运行方式

该游戏适合以单个 HTML 文件运行。

1. 将游戏 HTML 文件保存到本地。
2. 用浏览器打开该 HTML 文件。
3. 在菜单中选择语言。
4. 点击开始下潜。
5. 手机用户请将设备横向旋转。

不需要外部音频文件。
所有声音通过浏览器 WebAudio API 实时生成。

### 操作

手机：

- 拖动屏幕移动探测器。
- 横向拖动控制左右移动。
- 纵向拖动控制上下移动。
- 点击 PULSE 按钮释放声呐。

PC：

- 鼠标拖动可移动探测器。
- 也支持键盘操作。
- 方向键或 WASD 移动。
- 空格键释放声呐。

### 玩法

- 目标深度为 3200 米。
- 画面大部分时间处于黑暗。
- 声呐会短暂照亮被波面接触的地形。
- 通过声音反馈读取地形。
- 接触墙壁或岩石会损伤船体。
- 生物会响应声音并靠近声源。
- 移动和声呐使用会增加噪音。
- 噪音越高越容易被生物发现。
- 保持安静更安全。

### 存档

存档保存在浏览器 localStorage 中。

保存内容：

- depth：已到达深度
- log：探索日志
- lang：当前语言

中途退出后，可从菜单继续游戏。
语言设置也会保存。

### 支持语言

游戏支持：

- 日语：ja
- 英语：en
- 简体中文：zh
- 韩语：ko
- 西班牙语：es

可在菜单中切换语言。
切换后界面会重新绘制，并写入 localStorage。

### 技术说明

技术：

- Three.js
- WebGL
- GLSL Shader
- WebAudio API
- localStorage

图形策略：

- 场景由一条程序化隧道构成。
- 岩石使用 InstancedMesh。
- 生物使用少量网格。
- 使用距离遮罩着色器只绘制声呐波面。
- 渲染预算目标约为 50 draw calls / 90k triangles。

界面：

- 深度
- 船体耐久
- 噪音
- 用时
- 探索日志
- 语言选择
- 音频开关

---

## 한국어

### 개요

DEEP SIGNAL은 Three.js로 만든 웹 3D 소나 잠항 호러 게임입니다.
플레이어는 시야가 전혀 없는 해구로深海探査機를 조종합니다.
보통 화면은 완전히 어둡고, 소나 펄스가 닿는 지형만 잠시 렌더링됩니다.
생물은 소리에 반응하므로 조용히 잠항하는 것이 가장 안전한 경로입니다.

주요 기능:

- 시야 0의 3D 심해 환경
- 거리 마스크 셰이더 기반 소나 표현
- 소리에 반응하는 생물 AI
- 3D 오디오
- 모바일에서는 가로 화면으로 동작
- PC에서는 마우스와 키보드 지원
- 다국어 UI
- 로컬 세이브
- 예상 플레이 시간 8~12분

### 실행 방법

게임은 하나의 HTML 파일로 동작하도록 설계되었습니다.

1. 게임 HTML 파일을 로컬에 저장한다.
2. 브라우저에서 파일을 연다.
3. 메뉴에서 언어를 선택한다.
4. 잠항 시작을 누른다.
5. 모바일에서는 기기를 가로 방향으로 회전한다.

외부 오디오 파일은 필요하지 않습니다.
모든 소리는 브라우저의 WebAudio API로 실시간 생성됩니다.

### 조작

모바일:

- 화면을 드래그해 탐사선을 이동합니다.
- 가로 드래그는 좌우 이동입니다.
- 세로 드래그는 상하 이동입니다.
- PULSE 버튼으로 소나를 방출합니다.

PC:

- 마우스 드래그로 탐사선을 이동할 수 있습니다.
- 키보드 조작도 지원됩니다.
- 방향키 또는 WASD로 이동합니다.
- 스페이스바로 PULSE를 사용합니다.

### 플레이 방법

- 목표 깊이는 3200m입니다.
- 화면은 대부분 어둠입니다.
- 소나를 울리면 파면이 닿은 지형만 잠시 보입니다.
- 소음 피드백으로 지형을 파악합니다.
- 벽이나 바위에 부딪히면 선체가 손상됩니다.
- 생물은 소리에 반응해 접근합니다.
- 이동과 소나 사용은 소음을 높입니다.
- 소음이 높을수록 생물의 주목을 받기 쉽습니다.
- 조용히 이동하는 것이 안전합니다.

### 세이브

세이브 데이터는 브라우저 localStorage에 저장됩니다.

저장 항목:

- depth: 도달한 깊이
- log: 탐사 로그
- lang: 선택된 언어

중간에 종료해도 메뉴에서 이어서 시작할 수 있습니다.
언어 설정도 저장됩니다.

### 지원 언어

게임 지원 언어:

- 일본어: ja
- 영어: en
- 중국어 간체: zh
- 한국어: ko
- 스페인어: es

메뉴에서 언어를 변경할 수 있습니다.
변경 후 UI 문자열이 다시 그려지고 localStorage에 저장됩니다.

### 기술 사양

사용 기술:

- Three.js
- WebGL
- GLSL Shader
- WebAudio API
- localStorage

그래픽 정책:

- 환경은 하나의 절차적 터널로 구성됩니다.
- 바위는 InstancedMesh로 렌더링됩니다.
- 생물은 적은 수의 메시로 구성됩니다.
- 거리 마스크 셰이더로 소나 파면만 렌더링됩니다.
- 렌더 예산은 대략 50 draw calls / 90k triangles을 목표로 합니다.

UI:

- 심도
- 선체 내구성
- 소음
- 경과 시간
- 탐사 로그
- 언어 선택
- 오디오 ON/OFF

---

## Español

### Descripción

DEEP SIGNAL es un juego web de terror de sumergimiento con sonar, creado con Three.js.
El jugador controla una sonda de exploración profunda que desciende por una fosa sin visibilidad.
Normalmente la pantalla está oscura. El terreno solo aparece cuando una onda de sonar lo alcanza.
Las criaturas reaccionan al sonido, por lo que avanzar en silencio es la ruta más segura.

Características principales:

- Entorno submarino 3D sin visibilidad
- Shader de máscara de distancia para el sonar
- IA de criaturas reactiva al sonido
- Audio espacial
- Diseño horizontal para móviles
- Controles de ratón y teclado en PC
- Interfaz multilingüe
- Partida guardada local
- Duración estimada: 8 a 12 minutos

### Cómo ejecutar

El juego está pensado para ejecutarse como un único archivo HTML.

1. Guarda el archivo HTML del juego en tu equipo.
2. Ábrelo en un navegador.
3. Selecciona el idioma en el menú.
4. Pulsa para iniciar el descenso.
5. En móvil, gira el dispositivo a orientación horizontal.

No se necesitan archivos de audio externos.
Todos los sonidos se generan dinámicamente con la WebAudio API del navegador.

### Controles

Móvil:

- Arrastra la pantalla para mover la sonda.
- Arrastrar horizontalmente mueve izquierda y derecha.
- Arrastrar verticalmente mueve arriba y abajo.
- Pulsa PULSE para emitir sonar.

PC:

- Arrastra con el ratón para mover la sonda.
- También hay controles de teclado.
- Usa las flechas o WASD para moverte.
- Usa espacio para emitir un pulso de sonar.

### Juego

- La profundidad objetivo es 3200 metros.
- La pantalla está mayormente oscura.
- El sonar revela brevemente el terreno alcanzado por la onda.
- Debes interpretar el terreno mediante el sonido.
- Chocar contra paredes o rocas daña el casco.
- Las criaturas reaccionan al sonido y se acercan a la fuente.
- Moverse y usar sonar aumenta el ruido.
- Más ruido atrae más atención.
- Avanzar en silencio es más seguro.

### Guardado

El estado de la partida se guarda en el localStorage del navegador.

Campos guardados:

- depth: profundidad alcanzada
- log: registro de exploración
- lang: idioma seleccionado

Se puede continuar desde el menú.
El idioma también se guarda.

### Idiomas compatibles

El juego soporta:

- Japonés: ja
- Inglés: en
- Chino simplificado: zh
- Coreano: ko
- Español: es

El idioma puede cambiarse desde el menú.
Tras el cambio, la interfaz se redibuja y la configuración se guarda en localStorage.

### Notas técnicas

Tecnologías:

- Three.js
- WebGL
- GLSL shader
- WebAudio API
- localStorage

Política gráfica:

- El entorno es un túnel procedural.
- Las rocas se dibujan con InstancedMesh.
- Las criaturas usan una cantidad reducida de mallas.
- Un shader de máscara de distancia dibuja únicamente la onda del sonar.
- El presupuesto de renderizado apunta aproximadamente a 50 draw calls y 90k triángulos.

Interfaz:

- Profundidad
- Integridad del casco
- Nivel de ruido
- Tiempo transcurrido
- Registro de exploración
- Selector de idioma
- Activar o desactivar audio

---

## License /ライセンス /许可 /라이선스 /Licencia

この README.md の文章は、DEEP SIGNAL の対応言語向け説明ファイルとして提供されています。
プロジェクト全体のライセンスは、利用するリポジトリや配布条件に応じて別途指定してください。

This README text is provided as multilingual documentation for DEEP SIGNAL.
Specify a project license separately according to your repository or distribution requirements.

本 README 文本作为 DEEP SIGNAL 的多语言说明文件提供。
项目整体许可证请根据你的仓库或分发条件另行指定。

이 README 텍스트는 DEEP SIGNAL의 다국어 문서로 제공됩니다.
프로젝트 전체 라이선스는 저장소 또는 배포 조건에 따라 별도로 지정하십시오.

Este texto de README se ofrece como documentación multilingüe para DEEP SIGNAL.
Especifica una licencia para el proyecto por separado según tu repositorio o condiciones de distribución.