---
title: "方法 : 既存のテンプレートを更新する | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "項目テンプレート, 更新 (既存のテンプレートを)"
  - "プロジェクト テンプレート, 更新 (既存のテンプレートを)"
  - "Visual Studio のテンプレート, 更新 (既存のテンプレートを)"
ms.assetid: d585e45b-7fe2-45fa-9cf3-7f2bc060f3c4
caps.latest.revision: 19
caps.handback.revision: 19
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# 方法 : 既存のテンプレートを更新する
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

テンプレートを作成し、複数のファイルを .zip ファイルに圧縮した後で、テンプレートを変更できます。  それには、テンプレートのファイルを手動で変更するか、テンプレートに基づいてプロジェクトから新しいテンプレートをエクスポートします。  
  
## テンプレートのエクスポート ウィザードの使用による既存のテンプレートの更新  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] に用意されている**テンプレートのエクスポート** ウィザードを使用すると、既存のテンプレートを更新できます。  
  
#### テンプレートのエクスポートを使用して既存のテンプレートを更新するには  
  
1.  **\[ファイル\]** メニューの **\[新規作成\]** をポイントし、**\[新しいプロジェクト\]** をクリックします。  
  
2.  更新するテンプレートを選択し、一時プロジェクトの名前と場所を入力し、**\[OK\]** をクリックします。  
  
3.  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] でプロジェクトを変更します。  
  
4.  **\[ファイル\]** メニューの **\[テンプレートのエクスポート\]** をクリックし、**テンプレートのエクスポート** ウィザードを使用して新しいテンプレートを作成します。  
  
5.  更新されたテンプレートが .zip ファイルに圧縮されたら、古いテンプレートの .zip ファイルを削除します。  
  
## 既存のテンプレートの手動での更新  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] の外部で既存のテンプレートを更新するには、圧縮された .zip ファイル内のファイルを変更します。  
  
#### 既存のテンプレートを手動で更新するには  
  
1.  テンプレートを含む .zip ファイルを探します。  既定では、このファイルは \\My Documents\\Visual Studio *Version*\\My Exported Templates\\ にあります。  
  
2.  .zip ファイルを展開します。  
  
3.  現在のテンプレート ファイルを変更または削除するか、テンプレートに新しいファイルを追加します。  
  
4.  .vstemplate XML ファイルを開いたり、変更したり、保存したりして、更新された動作または新しいファイルを処理します。  .vstemplate スキーマの詳細については、「[Visual Studio テンプレート スキーマ参照](../extensibility/visual-studio-template-schema-reference.md)」を参照してください。  ソース ファイルで何をパラメーター化できるかの詳細については、「[テンプレート パラメーター](../ide/template-parameters.md)」を参照してください。  
  
5.  テンプレート内のファイルを選択して右クリックし、**\[送信\]** を選択し、**\[圧縮 \(zip 形式\) フォルダー\]** をクリックします。  選択したファイルは .zip ファイルに圧縮されます。  
  
6.  新しい .zip ファイルを古い .zip ファイルと同じディレクトリに配置します。  
  
7.  抽出したテンプレート ファイルと古いテンプレート .zip ファイルを削除します。  
  
8.  \(\[スタート\] メニューの **\[Visual Studio 2010\]、\[Visual Studio Tools\]、\[開発者コマンド プロンプト\]** から\) 開発者コマンド プロンプトのインスタンスを \(管理者として\) 開きます。  
  
9. 次のコマンドを実行します: `devenv /installvstemplates`  
  
## 参照  
 [テンプレートのカスタマイズ](../ide/customizing-project-and-item-templates.md)   
 [カスタム プロジェクトと項目テンプレートの作成](../ide/creating-project-and-item-templates.md)   
 [Visual Studio テンプレート スキーマ参照](../extensibility/visual-studio-template-schema-reference.md)   
 [テンプレート パラメーター](../ide/template-parameters.md)   
 [方法 : スタート キットを作成する](../ide/how-to-create-starter-kits.md)