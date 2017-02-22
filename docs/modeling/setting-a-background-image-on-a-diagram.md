---
title: "ダイアグラムへの背景イメージの設定 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e334a24c-8521-4072-b50f-e59158dde145
caps.latest.revision: 2
caps.handback.revision: 2
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
---
# ダイアグラムへの背景イメージの設定
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Visualization and Modeling SDK では、カスタム コードを使用して生成されるデザイナーの背景イメージを設定できます。  
  
## 背景イメージの設定  
  
#### 生成されるデザイナーの背景イメージを設定するには  
  
1.  図の背景として使用するイメージ ファイルを、現在のプロジェクトの Dsl\\Resources ディレクトリにコピーします。  
  
2.  **ソリューション エクスプローラー**で Dsl\\Resources フォルダーを右クリックし、**\[追加\]** をポイントして、**\[既存の項目\]** をクリックします。  
  
3.  **\[既存項目の追加\]** ダイアログ ボックスで Dsl\\Resources フォルダーを参照します。  
  
4.  **\[ファイルの種類\]** リストで、**\[イメージ ファイル\]** をクリックします。  
  
5.  ディレクトリにコピーしたイメージ ファイルをクリックして、**［追加］** をクリックします。  
  
6.  Dsl を右クリックし、**［プロパティ］** をクリックして、Dsl プロジェクトのプロパティを開きます。  
  
7.  **［リソース］** タブで **［このプロジェクトには既定のリソース ファイルが含まれていません。ファイルを作成するには、ここをクリックしてください。\]** をクリックします。  
  
8.  **ソリューション エクスプローラー**からリソース ウィンドウに画像をドラッグして、イメージ ファイルをリソース ファイルに追加します。  
  
9. ［ファイル］ メニューを開き、プロジェクトのプロパティを保存するオプションをクリックします。  
  
10. ファイル Dsl\\Properties\\Resources.resx が存在しており、その下に Resources.Designer.cs ファイルがあることを確認します。  
  
11. Resources.Designer.cs が欠落している場合は、**ソリューション エクスプローラー**で Resources.resx ファイルをクリックします。  
  
12. **\[プロパティ\]** ウィンドウで、`Custom Tool` プロパティを `ResXFileCodeGenerator` に設定します。  
  
13. **ソリューション エクスプローラー**で Dsl プロジェクトを右クリックし、**\[追加\]** をポイントして、**\[新しいフォルダー\]** をクリックします。  
  
14. フォルダーに Custom という名前を指定します。  
  
15. ［Custom］ フォルダーを右クリックし、**\[追加\]** をポイントして、**\[新しい項目\]** をクリックします。  
  
16. **\[新しい項目の追加\]** ダイアログ ボックスの **\[テンプレート\]** リストで、**\[コード ファイル\]** をクリックします。  
  
17. **\[名前\]** ボックスに「`BackgroundImage.cs`」と入力し、**\[追加\]** をクリックします。  
  
18. 次のコードを BackgroundImage.cs ファイルにコピーし、名前空間、図クラス名、およびイメージ ファイル リソース名を調整します。  
  
     "MyDiagramClass" を、Dsl\\GeneratedCode\\Diagrams.cs で定義されている図の部分クラスの名前に置き換えます。  Dsl\\GeneratedCode\\Diagrams.cs ファイルから正しい名前空間を取得することもできます。  
  
    ```  
    using System;  
    using Microsoft.VisualStudio.Modeling.Diagrams;  
  
    // Fix the namespace:  
    namespace Fabrikam.MyLanguage  
    {  
      // Fix the Diagram Class name - get it from GeneratedCode\Diagram.cs  
  
      public partial class Language29Diagram  
      {  
        protected override void InitializeInstanceResources()  
        {  
          // Fix the Resources namespace and the Image resource name:  
          ImageField backgroundField = new ImageField("background",  
              Fabrikam.MyLanguage.Properties.Resources.MyPicture);  
  
          backgroundField.DefaultFocusable = false;  
          backgroundField.DefaultSelectable = false;  
          backgroundField.DefaultVisibility = true;  
          backgroundField.DefaultUnscaled = false;  
  
          shapeFields.Add(backgroundField);  
  
          backgroundField.AnchoringBehavior  
            .SetTopAnchor(AnchoringBehavior.Edge.Top, 0.01);  
          backgroundField.AnchoringBehavior  
            .SetLeftAnchor(AnchoringBehavior.Edge.Left, 0.01);  
          backgroundField.AnchoringBehavior  
            .SetRightAnchor(AnchoringBehavior.Edge.Right, 0.01);  
          backgroundField.AnchoringBehavior  
            .SetBottomAnchor(AnchoringBehavior.Edge.Bottom, 0.01);  
  
          base.InitializeInstanceResources();  
        }  
      }  
    }  
    ```  
  
     プログラム コードを使用したモデルのカスタマイズの詳細については、「[プログラム コードにおけるモデル内の移動およびモデルの更新](../modeling/navigating-and-updating-a-model-in-program-code.md)」を参照してください。  
  
## 参照  
 [シェイプとコネクタの定義](../modeling/defining-shapes-and-connectors.md)   
 [テキストおよびイメージ フィールドのカスタマイズ](../modeling/customizing-text-and-image-fields.md)   
 [プログラム コードにおけるモデル内の移動およびモデルの更新](../modeling/navigating-and-updating-a-model-in-program-code.md)   
 [ドメイン固有言語をカスタマイズするコードの記述](../modeling/writing-code-to-customise-a-domain-specific-language.md)