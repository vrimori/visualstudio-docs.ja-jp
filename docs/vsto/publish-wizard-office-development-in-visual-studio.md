---
title: "発行ウィザード (Visual Studio での Office 開発)"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VST.ProjectProperties.PublishWizard"
  - "VST.PublishWizard.Publish.2007System"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "ClickOnce 配置 [Visual Studio での Office 開発]、発行ウィザード"
  - "アプリケーションの配置 [Visual Studio での Office 開発]、発行ウィザード"
  - "Office アプリケーション [Visual Studio での Office 開発]、発行ウィザード"
  - "発行ウィザード、Office ソリューション"
ms.assetid: 793314b6-b6a6-4509-8f1c-dd9466cf5190
caps.latest.revision: 17
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 13
---
# 発行ウィザード (Visual Studio での Office 開発)
  指定した場所にソリューション ファイルをコピーするに **発行ウィザード** を使用してマニフェスト ファイルやセットアップ プログラムを作成します。  
  
 このウィザードに、 **ビルド** のメニューにアクセスするには、 **発行** *ソリューション名*を選択します。  **ソリューション エクスプローラー**から**発行ウィザード**にアクセスすることもできます。  プロジェクト ノードのショートカット メニューを開き、 **発行**を選択します。  
  
 以下の各セクションでは、ウィザードのページについて説明します。  
  
## \[アプリケーションをどこに発行しますか?\]  
 **\[このアプリケーションを発行する場所を指定してください\]**  
 必ず指定します。  発行場所は、**発行ウィザード**がソリューション ファイル \(マニュフェスト、アセンブリ、一時的な証明書、ビルドのその他のファイルなど\) をコピーする先のディレクトリです。  このディレクトリに対する書き込みアクセスが必要です。  
  
 場所は、ディスク パス、ファイル共有、 FTP サイト、または Web サイトの URL として入力するか、場所の参照するに **参照** のボタンをクリックします。  パスは、次の形式で指定します。  
  
-   標準的な Windows 形式の相対パスまたは絶対パス \(たとえば C:\\Deploy\\MyApplication または \\MyApplication\)  
  
-   UNC \(Universal Naming Convention\) パス \(たとえば \\\\ServerName\\MyApplication\\\)  
  
-   http:\/\/www.microsoft.com\/MyApplication などの Web サイトの URL。  
  
 既定では、IIS がインストールされている場合の発行場所は *http:\/\/localhost\/projectname\/* で、IIS がインストールされていない場合の発行場所は publish\\ directory ディレクトリになります。  
  
> [!NOTE]  
>  ターゲット コンピューターで Windows Vista が実行されている場合は、さらに考慮すべき事項があります。  ローカルな発行オプションを使用するには、Windows Vista コンピューターに管理者としてログオンすることが必要です。  また、IIS がインストールされているかどうかにかかわらず、既定の場所は常に *publish\\* ディレクトリになります。  
  
## \[エンド ユーザーのコンピューター上での、既定のインストール パスを指定してください\]  
 インストール パスは省略できます。  インストール パスは、後で設定することもできます。  詳細については、「[方法: Office ソリューションのインストール パスを変更する](http://msdn.microsoft.com/ja-jp/d0eaa07b-2d72-4902-899f-2f9fb165b8fd)」を参照してください。  
  
 インストール パスは、エンド ユーザーがカスタマイズのインストールを実行するディレクトリです。  更新プログラムのチェックを行うためにソリューションが使用するパスでもあります。  この場所が、前のページの **\[このアプリケーションを発行する場所を指定してください\]** ボックスに入力したパスと同じでない限り、**発行ウィザード**はこの場所にソリューションを配置しません。  
  
 **\[Web サイトから\]**  
 エンド ユーザーがソリューションをインストールするのに使用する URL を指定します。  
  
 **\[UNC パスまたはファイル共有から\]**  
 エンド ユーザーがソリューションをインストールするのに使用する UNC パスを指定します。  
  
 **\[CD\-ROM または DVD\-ROM から\]**  
 このオプションの場合、インストール パスは必要ありません。  
  
 Visual Studio は CD または DVD への書き込みを行いません。  出力を手動で CD または DVD にコピーする必要があります。  
  
## 参照  
 [ClickOnce を使用した Office ソリューションの配置](../vsto/deploying-an-office-solution-by-using-clickonce.md)   
 [プロジェクト デザイナーの &#91;発行&#93; ページ &#40;Visual Studio での Office 開発&#41;](../vsto/publish-page-project-designer-office-development-in-visual-studio.md)   
 [Office ソリューションの配置](../vsto/deploying-an-office-solution.md)  
  
  