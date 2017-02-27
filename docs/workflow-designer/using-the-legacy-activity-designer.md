---
title: "従来のアクティビティ デザイナーの使用 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "アクティビティ, 子の追加"
  - "アクティビティ, 構成"
  - "アクティビティ, カスタムの作成"
  - "アクティビティ デザイナー"
  - "子アクティビティ, 追加"
  - "カスタム アクティビティ"
ms.assetid: 2fea8a05-6e58-423d-94bf-a822b15ffb80
caps.latest.revision: 5
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# 従来のアクティビティ デザイナーの使用
このトピックでは、従来の [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)]でアクティビティ デザイナーを使用する方法について説明します。[!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] または [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)] を対象とする場合は、従来のデザイナーを使用します。  
  
 アクティビティ デザイナーを使用すると、独自のカスタム アクティビティを作成できます。  
  
## カスタム アクティビティの作成  
 アクティビティ デザイナを使ってカスタム アクティビティを作成するには、次の手順に従います。  
  
1.  **\[プロジェクト\]** メニューの **\[アクティビティの追加\]** をクリックします。  
  
2.  **\[アクティビティ\]** または **\[アクティビティ \(コード分離付き\)\]** テンプレートを選択します。  
  
    1.  アクティビティ定義とユーザー コードが同じコード ファイルに入ったアクティビティを作成するには、**\[アクティビティ\]** テンプレートを使用します。  
  
    2.  アクティビティ定義がワークフロー マークアップとして表記され、ユーザー コードが別のコード ファイルに格納されるアクティビティを作成するには、**\[アクティビティ \(コード分離付き\)\]** テンプレートを使用します。  
  
3.  アクティビティ名を入力するか、既定の名前を受け入れて、**\[追加\]** をクリックします。  
  
 また、**Workflow Activity Library** 型の新しいプロジェクトを作成することにより、カスタム アクティビティのセットを作成できます。このプロジェクトの種類の詳細については、「[方法: ワークフロー アクティビティ ライブラリを作成する \(レガシ\)](../Topic/How%20to:%20Create%20a%20Workflow%20Activity%20Library%20\(Legacy\).md)」を参照してください。  
  
## アクティビティの構成  
 アクティビティ デザイナがアクティブであるときに、プロパティ ブラウザを使用すると、次の表にリストされているプロパティを構成できます。  
  
|プロパティ|コメント|  
|-----------|----------|  
|**Name**|アクティビティの名前。|  
|**Base Class**|アクティビティの派生元の基本クラス。既定の基本クラスは [SequenceActivity](http://go.microsoft.com/fwlink?LinkID=65020) です。**\[プロパティ\]** ウィンドウで、**\[基本クラス\]** の **\[...\]** をクリックすると、[\[.NET 型の参照と選択\] ダイアログ ボックス \(レガシ\)](../Topic/Browse%20and%20Select%20a%20.NET%20Type%20Dialog%20Box%20\(Legacy\).md)で別の基本クラスを選択できます。|  
|**Description**|アクティビティに関するユーザー定義の説明。|  
|**Enabled**|既定では **True** に設定され、アクティビティの実行と検証が有効です。**False** に設定すると、アクティビティの実行と検証が無効になります。アクティビティの実行と検証の詳細については、「[ワークフロー アクティビティの開発](http://go.microsoft.com/fwlink?LinkID=65024)」を参照してください。|  
  
## 子アクティビティの追加  
 子アクティビティを、ツールボックスから設計中のアクティビティまでドラッグすることができます。その後、プロパティ ブラウザを使ってそれぞれの子アクティビティを構成できます。  
  
## 参照  
 [ワークフロー アクティビティの開発](http://go.microsoft.com/fwlink?LinkID=65024)   
 [カスタム アクティビティの作成](http://go.microsoft.com/fwlink?LinkID=65021)   
 [従来のワークフロー アクティビティ](../workflow-designer/legacy-workflow-activities.md)   
 [カスタム アクティビティのサンプル](http://go.microsoft.com/fwlink?LinkID=65022)   
 [方法: ワークフロー アクティビティ ライブラリを作成する \(レガシ\)](../Topic/How%20to:%20Create%20a%20Workflow%20Activity%20Library%20\(Legacy\).md)   
 [従来のワークフロー デザイナーの使用](../workflow-designer/using-the-legacy-workflow-designer.md)