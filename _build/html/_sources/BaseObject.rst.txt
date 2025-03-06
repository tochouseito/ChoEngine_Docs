BaseObject
============================

このセクションでは、BaseObjectの基本的な使い方を解説します。

オブジェクトを描画するまでの手順

１．3Dオブジェクトとして利用するクラスにBaseObjectを継承させます
.. code-block:: cpp

   #include "Game/Scripts/Objects/BaseObject/BaseObject.h"

    class Object : public BaseObject
    {
    public:/*method*/
	    // BaseObject を介して継承されました
	    void Initialize() override;
	    void Update() override;
    private:/*member*/
    };

２．ObjectクラスをGameSceneに持たせます

３．GameSceneでObjectのインスタンスを生成した後、BaseObjectのCreate関数で描画に必要なリソースを生成します。
.. code-block:: cpp

    void GameScene::Initialize(){

    // ここはGameSceneセクションで解説します
    SceneManager* sceneManager = GetSceneManager();
    ComponentManager* componentManager = sceneManager->GetCompPtr();
    input = sceneManager->GetInputManagerPtr();

    m_Object = std::make_unique<Object>();
    m_Object->Create("player", sceneManager, componentManager, input);
    // ここからObjectの初期化処理
    // 例
    m_Object->Initialize();

    }

Create関数は
Create(Objectの名前、sceneManagerのポインタ、componentManagerのポインタ、inputのポインタ)
の引数で構成されています。

Objectの名前 : Engine内でのデータ名。ObjectListに表示される名前。
sceneManagerPtr : 
componentManagerPtr : 
inputPtr : 入力関数を使用するためのインタフェース

