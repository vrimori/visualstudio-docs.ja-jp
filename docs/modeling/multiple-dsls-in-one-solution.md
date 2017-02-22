---
title: "1 つのソリューション内の複数の DSL | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7e668620-6217-4e87-aea7-e9036776c8e4
caps.latest.revision: 3
caps.handback.revision: 3
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
---
# 1 つのソリューション内の複数の DSL
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

いくつかの DSL を単一ソリューションの一部としてパッケージ化し、同時にインストールすることができます。  
  
 複数の DSL を統合するためにいくつかの手法を使用できます。  詳細については、「[Visual Studio Modelbus を使用して、モデルの統合](../modeling/integrating-models-by-using-visual-studio-modelbus.md)」、「[方法: ドラッグ アンド ドロップ ハンドラーを追加する](../modeling/how-to-add-a-drag-and-drop-handler.md)」、および「[コピー動作のカスタマイズ](../modeling/customizing-copy-behavior.md)」を参照してください。  
  
### 複数の DSL を同じソリューションの中にビルドするには  
  
1.  2 つ以上の DSL ソリューションと 1 つの VSIX プロジェクトを作成し、すべてのプロジェクトを単一のソリューションに追加します。  
  
    -   新しい VSIX プロジェクトを作成するには、**\[新しいプロジェクト\]** ダイアログ ボックスで、**\[Visual C\#\]**、**\[機能拡張\]**、**\[VSIX プロジェクト\]** の順にクリックします。  
  
    -   VSIX ソリューション ディレクトリ内に 2 つ以上の DSL ソリューションを作成します。  
  
         各 DSL について、Visual Studio の新しいインスタンスを開きます。  新しい DSL を作成し、同じソリューション フォルダとして VSIX ソリューションを指定します。  
  
         各 DSL は異なるファイル拡張子名を付けて作成します。  
  
    -   **\[Dsl\]** プロジェクトおよび **\[DslPackage\]** プロジェクトの名前はすべて異なるように変更します。  たとえば、`Dsl1`、`DslPackage1`、`Dsl2`、`DslPackage2` とします。  
  
    -   それぞれの **DslPackage\*\\source.extension.tt** で、この行を次に示す正しい Dsl プロジェクト名に更新します。  
  
         `string dslProjectName = "Dsl2";`  
  
    -   VSIX ソリューションで、Dsl\* プロジェクトおよび DslPackage\* プロジェクトを追加します。  
  
         各ペアを独自のソリューション フォルダーに配置することを推奨します。  
  
2.  以下のように DSL の VSIX マニフェストを結合します。  
  
    1.  *YourVsixProject* **\\source.extension.manifest** を開きます。  
  
    2.  各 DSL に対して、**\[コンテンツの追加\]** を選択し、以下のように追加します。  
  
        -   **\[MEF コンポーネント\]** として `Dsl*` プロジェクト  
  
        -   **\[MEF コンポーネント\]** として `DslPackage*` プロジェクト  
  
        -   **\[VS パッケージ\]** として `DslPackage*` プロジェクト  
  
3.  ソリューションをビルドします。  
  
 この結果の VSIX では両方の DSL がインストールされます。  F5 を使用してテストするか、*YourVsixProject***\\bin\\Debug\\\*.vsix** を配置できます。  
  
## 参照  
 [Visual Studio Modelbus を使用して、モデルの統合](../modeling/integrating-models-by-using-visual-studio-modelbus.md)   
 [方法: ドラッグ アンド ドロップ ハンドラーを追加する](../modeling/how-to-add-a-drag-and-drop-handler.md)   
 [コピー動作のカスタマイズ](../modeling/customizing-copy-behavior.md)