---
title: "Web パーツまたはアプリケーション ページの再利用できるコントロールの作成"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Visual Studio での SharePoint 開発, ユーザー コントロール"
  - "ユーザー コントロール [Visual Studio での SharePoint 開発], 作成"
ms.assetid: 8fcafd98-c002-47f1-b4a9-cbb500232616
caps.latest.revision: 19
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 19
---
# Web パーツまたはアプリケーション ページの再利用できるコントロールの作成
  Visual Studio では、カスタム、SharePoint で実行されるアプリケーション ページと Web パーツ使用できる再利用可能なカスタム コントロールを作成できます。  このようなコントロールは、ユーザー コントロールと呼ばれます。  ユーザー コントロールの詳細については、「[ASP.NET User Controls](../Topic/ASP.NET%20User%20Controls.md)」を参照してください。  
  
## ユーザー コントロールの作成  
 ユーザー コントロールを作成するには、**空の SharePoint プロジェクト**に**ユーザー コントロール**を追加します。  詳細については、「[方法: SharePoint アプリケーション ページまたは Web パーツのユーザー コントロールを作成する](../sharepoint/how-to-create-a-user-control-for-a-sharepoint-application-page-or-web-part.md)」を参照してください。  
  
 **ユーザー コントロール**項目を追加すると、プロジェクトにフォルダーが作成され、そのフォルダーにいくつかのファイルが追加されます。  各ファイルの説明を次の表に示します。  
  
|File|説明|  
|----------|--------|  
|ユーザー コントロール ファイル|ユーザー コントロールを定義します。  コントロールとマークアップをこのファイルに追加して、ユーザー コントロールをデザインします。|  
|コード ファイル|ユーザー コントロールに分離コードを含めます。  このファイルにイベントを処理するコードを追加します。|  
|デザイナー コード ファイル|デザイナーによって生成されるコードが格納されます。直接編集することはできません。|  
  
## ユーザー コントロールのデザイン  
 Visual Studio の Visual Web Developer デザイナーを使用してユーザー コントロールをデザインします。  このデザイナーは、プロジェクトのユーザー コントロール ファイルを開き、**\[デザイン\]** タブをクリックすると表示されます。  このデザイナーの使用方法の詳細については、「[Visual Studio Web Development Content Map](http://msdn.microsoft.com/ja-jp/9c31f93b-c8fb-4599-9b14-6194ec8c7539)」を参照してください。  
  
## ユーザー コントロールの使用  
 アプリケーション ページまたは Web パーツにユーザー コントロールを含めるまで、ユーザー コントロールは SharePoint に表示されません。  
  
 ユーザー コントロールをアプリケーション ページに含めるには、[@ Register](http://msdn.microsoft.com/ja-jp/66f34922-be41-4e36-9dc8-1774d85311d1) ディレクティブをアプリケーション ページに追加した後、ページ内の 1 つ以上のコンテンツ プレースホルダーの内部でユーザー コントロールを宣言します。  このタスクを標準的な ASP.NET Web ページで実現する方法の例については、「[How to: Include a User Control in an ASP.NET Web Page](../Topic/How%20to:%20Include%20a%20User%20Control%20in%20an%20ASP.NET%20Web%20Page.md)」を参照してください。  
  
 Web パーツにユーザー コントロールを含めるには、Web パーツ コード ファイルの Web パーツ <xref:System.Web.UI.WebControls.WebParts.Part.Controls%2A> コレクションにユーザー コントロールを追加します。  次の例では、Web パーツの <xref:System.Web.UI.WebControls.WebParts.Part.Controls%2A> コレクションにユーザー コントロールを追加します。  
  
 [!code-csharp[SP_VisualWebPart#5](../snippets/csharp/VS_Snippets_OfficeSP/sp_visualwebpart/cs/visualwebpart1/visualwebpart1.cs#5)]
 [!code-vb[SP_VisualWebPart#5](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_visualwebpart/vb/visualwebpart1/visualwebpart1.vb#5)]  
  
## ユーザー コントロールのデバッグ  
 ユーザー コントロールをデバッグするには、SharePoint プロジェクトのアプリケーション ページまたは Web パーツにユーザー コントロールが含まれていることを確認します。  Visual Studio プロジェクトでコードをデバッグする場合と同様に、ユーザー コントロールのコードをデバッグできます。  
  
 Visual Studio デバッガーを開始すると、SharePoint サイトが開きます。  
  
 SharePoint で、ユーザー コントロールを含むアプリケーション ページを開きます。  ユーザー コントロールが Web パーツに含まれる場合、SharePoint の Web パーツ ページに Web パーツを追加します。  
  
 SharePoint プロジェクトのデバッグの詳細については、「[SharePoint ソリューションのトラブルシューティング](../sharepoint/troubleshooting-sharepoint-solutions.md)」を参照してください。  
  
## 関連トピック  
  
|タイトル|説明|  
|----------|--------|  
|[方法: SharePoint アプリケーション ページまたは Web パーツのユーザー コントロールを作成する](../sharepoint/how-to-create-a-user-control-for-a-sharepoint-application-page-or-web-part.md)|SharePoint で実行されるアプリケーション ページと Web パーツから使用できる再利用可能なカスタム コントロールを作成する方法について説明します。|  
|[Visual Web Developer の操作](http://msdn.microsoft.com/ja-jp/9c31f93b-c8fb-4599-9b14-6194ec8c7539)|プロジェクトで Web ページを開くと表示されるデザイナーの使用方法について説明します。|  
  
  