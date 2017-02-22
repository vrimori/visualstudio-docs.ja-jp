---
title: "方法 : テンプレートの問題を解決する | Microsoft Docs"
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
  - "Visual Studio のテンプレート, トラブルシューティング"
ms.assetid: 3e577ad2-f725-4c11-93b3-477f2404ec81
caps.latest.revision: 10
caps.handback.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# 方法 : テンプレートの問題を解決する
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

テンプレートを開発環境に読み込むことができない場合、問題を突き止めるにはいくつかの方法があります。  
  
## .vstemplate ファイルの検証  
 テンプレートの .vstemplate ファイルが [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] テンプレート スキーマに準拠していないと、テンプレートが **\[新しいプロジェクト\]** ダイアログ ボックスに表示されないことがあります。  
  
#### .vstemplate ファイルを検証するには  
  
1.  テンプレートを含む .zip ファイルを探します。  
  
2.  .zip ファイルを展開します。  
  
3.  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] の **\[ファイル\]** メニューの **\[開く\]** をクリックし、**\[ファイル\]** をクリックします。  
  
4.  テンプレートの .vstemplate ファイルを選択し、**\[開く\]** をクリックします。  
  
5.  .vstemplate ファイルの XML が [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] テンプレート スキーマに準拠していることを確認します。  .vstemplate スキーマの詳細については、「[Visual Studio テンプレート スキーマ参照](../extensibility/visual-studio-template-schema-reference.md)」を参照してください。  
  
    > [!NOTE]
    >  .vstemplate ファイルを編集する際に IntelliSense のサポートを利用するには、`xmlns` 属性を `VSTemplate` 要素に追加し、http:\/\/schemas.microsoft.com\/developer\/vstemplate\/2005 の値を割り当てます。  
  
6.  .vstemplate ファイルを保存して、閉じます。  
  
7.  テンプレートに含まれるファイルを選択して右クリックし、**\[送る\]** をポイントし、**\[圧縮 \(zip 形式\) フォルダー\]** をクリックします。  選択したファイルは .zip ファイルに圧縮されます。  
  
8.  新しい .zip ファイルを古い .zip ファイルと同じディレクトリに配置します。  
  
9. 抽出したテンプレート ファイルと古いテンプレート .zip ファイルを削除します。  
  
## イベント ログの監視  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] は、テンプレート .zip ファイルの処理中に発生したエラーを記録します。  **\[新しいプロジェクト\]** ダイアログ ボックスに表示されるはずのテンプレートが表示されない場合は、**\[イベント ビューアー\]** を使用して問題を解決できます。  
  
#### イベント ビューアーでテンプレート エラーを見つけるには  
  
1.  Windows で、**\[スタート\]** をクリックし、**\[コントロール パネル\]** をクリックします。次に、**\[管理ツール\]** をダブルクリックし、**\[イベント ビューアー\]** をダブルクリックします。  
  
2.  左のペインで、**\[アプリケーション\]** をクリックします。  
  
3.  **\[ソース\]** の値が \[`Visual Studio - VsTemplate`\] のイベントを探します。  
  
4.  テンプレート イベントをダブルクリックして、エラーを表示します。  
  
## 参照  
 [テンプレートのカスタマイズ](../ide/customizing-project-and-item-templates.md)   
 [カスタム プロジェクトと項目テンプレートの作成](../ide/creating-project-and-item-templates.md)   
 [Visual Studio テンプレート スキーマ参照](../extensibility/visual-studio-template-schema-reference.md)