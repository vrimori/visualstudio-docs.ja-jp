---
title: "チュートリアル: カスタム エディターの作成 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "エディター [Visual Studio SDK] - カスタム作成します。"
ms.assetid: d090abb6-d99f-4083-a3db-cd16bf81ce7d
caps.latest.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 17
---
# チュートリアル: カスタム エディターの作成
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

VSPackage プロジェクト テンプレートは、C\+\+ では、単純なカスタム エディターを作成できます。  VSPackage プロジェクト テンプレートは、c\# または Visual Basic のプロジェクトをサポートしていません。 詳細については、「[Visual Studio SDK](../extensibility/visual-studio-sdk.md)」を参照してください。  
  
## 必須コンポーネント  
 このチュートリアルを行うには、Visual Studio SDK をインストールする必要があります。 詳細については、「[Visual Studio SDK をインストールします。](../extensibility/installing-the-visual-studio-sdk.md)」を参照してください。  
  
## Visual Studio パッケージ プロジェクト テンプレート  
 Visual Studio パッケージ プロジェクト テンプレートは記載されて、 **新しいプロジェクト** C\+\+ の機能拡張フォルダー\] ダイアログ ボックス  
  
### Visual Studio パッケージ テンプレートを使用して VSPackage を作成するには  
  
1.  Visual Studio パッケージ テンプレートを使用して、プロジェクトを作成します。  
  
2.  選択、 **カスタム エディター** と\] チェック ボックスをクリックして **次**します。**エディター オプション** ページが表示されます。  
  
3.  エディターでの名前を入力、 **エディター名** ボックス。 エディターに関連付けるファイル拡張子を入力、 **ファイル拡張子** ボックス。 エディターは、この拡張子のファイルに使用できます。 ファイル拡張子が Windows ではなくのみ、Visual Studio に登録されます。 エディターで作成された新しいドキュメントの既定のファイル名を入力、 **既定のファイル名** ボックス。  
  
4.  **\[完了\]** をクリックして、指定したフォルダーに VSPackage を作成します。  
  
### カスタム エディターをテストするには  
  
1.  **ファイル** \] メニューをポイント **新規** \] をクリックし、 **ファイル**します。  
  
2.  **インストールされたテンプレート** のウィンドウ、 **新しいファイル** ダイアログ ボックスで選択し、ファイル テンプレート、ファイルの種類を登録します。  
  
3.  クリックして **開く** 、ドキュメントを表示および編集します。  
  
     エディターには、切り取りと貼り付け、検索と置換、および開くアンド ロード操作がサポートしています。  
  
## 参照  
 [Vspackages にあります。](../extensibility/internals/vspackages.md)