BaseObject
==========

このセクションでは、BaseObjectの基本的な使い方を解説します。

オブジェクトを描画するまでの手順
---------------------------------

1. 3Dオブジェクトとして利用するクラスにBaseObjectを継承させます。

.. code-block:: cpp

    #include "Game/Scripts/Objects/BaseObject/BaseObject.h"

    class Object : public BaseObject {
        public:
            void Initialize() override;
            void Update() override;
    };

2. ObjectクラスをGameSceneに持たせます。

3. GameSceneでObjectのインスタンスを生成した後、BaseObjectのCreate関数で描画に必要なリソースを生成します。

.. code-block:: cpp

    void GameScene::Initialize() {
        SceneManager* sceneManager = GetSceneManager();
        ComponentManager* componentManager = sceneManager->GetCompPtr();
        input = sceneManager->GetInputManagerPtr();

        m_Object = std::make_unique<Object>();
        m_Object->Create("player", sceneManager, componentManager, input);
        m_Object->Initialize();
    }

Create関数の第一引数はEngineが扱うObjectの名前で、ObjectListに表示される名前はこれになります。

これでObjectの描画ができます！

オブジェクトのコンポーネント
---------------------------------

BaseObjectには以下のコンポーネントが含まれています

transform : 位置、角度、スケール
mesh : 
material : 
render : 
animation : 

1. Transform

2. Mesh : 

3. Material : 

4. Render : 

5. Animation : 

---