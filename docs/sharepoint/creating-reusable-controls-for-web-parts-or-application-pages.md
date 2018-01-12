---
title: "Web パーツまたはアプリケーション ページの再利用可能なコントロールの作成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- user controls [SharePoint development in Visual Studio], creating
- SharePoint development in Visual Studio, user controls
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 4818c9519920d722230b2d8a44d7945511931173
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/10/2018
---
# <a name="creating-reusable-controls-for-web-parts-or-application-pages"></a>Web パーツまたはアプリケーション ページの再利用できるコントロールの作成
  Visual Studio で、アプリケーション ページと SharePoint で実行される Web パーツで使用できる、再利用可能なカスタム コントロールを作成することができます。 これらのコントロールは、ユーザー コントロールと呼ばれます。 ユーザー コントロールは、ASP.NET Web ページと同様に動作する複合コントロールの種類: ユーザー コントロールを既存の Web サーバー コントロールとマークアップを追加し、コントロールのプロパティとメソッドを定義できます。 ASP.NET Web ページで、場所、単位として機能し、埋め込むことができます。  
  
## <a name="creating-a-user-control"></a>ユーザー コントロールの作成  
 ユーザー コントロールを作成するには追加、**ユーザー コントロール**を**空の SharePoint プロジェクト**です。 詳細については、次を参照してください。[する方法: SharePoint アプリケーション ページや Web パーツのユーザー コントロールを作成](../sharepoint/how-to-create-a-user-control-for-a-sharepoint-application-page-or-web-part.md)です。  
  
 追加すると、**ユーザー コントロール**項目、Visual Studio は、プロジェクトのフォルダーが作成され、フォルダーにいくつかのファイルを追加します。 各ファイルの説明を次の表に示します。  
  
|ファイル|説明|  
|----------|-----------------|  
|ユーザー コントロール ファイル|ユーザー コントロールを定義します。 このファイルへのコントロールとマークアップを追加することでユーザー コントロールをデザインします。|  
|コード ファイル|ユーザー コントロールの分離コードが含まれています。 このファイルにイベントを処理するコードを追加します。|  
|デザイナー コード ファイル|デザイナーによって生成されたコードが含まれており、直接を編集しないでください。|  
  
## <a name="designing-the-user-control"></a>ユーザー コントロールのデザイン  
 Visual Studio で Visual Web Developer デザイナーを使用してユーザー コントロールをデザインします。 プロジェクトのユーザー コントロール ファイルを開きますを選択すると、このデザイナーが表示されます、**デザイン**タブです。  

## <a name="consuming-the-user-control"></a>ユーザー コントロールの使用  
 SharePoint では、アプリケーション ページまたは Web パーツに含まれるまで、ユーザー コントロールは表示されません。  
  
 アプリケーション ページで、ユーザー コントロールを含めるには、ASP.NET ユーザー コントロールを追加する Web ページを開きます。 デザイン ビューに切り替えます、ソリューション エクスプ ローラーで、カスタム ユーザー コントロール ファイルを選択し、ページにドラッグします。 ASP.NET ユーザー コントロールがページに追加し、デザイナーは、ユーザー コントロールを認識するように、ページに必要な @ Register ディレクティブを作成します。 コントロールのパブリック プロパティとメソッドを使用できますようになりました。  
  
 Web パーツのユーザー コントロールを含めるには、Web パーツにユーザー コントロールを追加<xref:System.Web.UI.WebControls.WebParts.Part.Controls%2A>Web パーツ コード ファイル内のコレクション。 次の例では、ユーザー コントロールを<xref:System.Web.UI.WebControls.WebParts.Part.Controls%2A>Web パーツのコレクション。  
  
 [!code-vb[SP_VisualWebPart#5](../sharepoint/codesnippet/VisualBasic/sp_visualwebpart.vb/visualwebpart1/visualwebpart1.vb#5)]
 [!code-csharp[SP_VisualWebPart#5](../sharepoint/codesnippet/CSharp/sp_visualwebpart.cs/visualwebpart1/visualwebpart1.cs#5)]  
  
## <a name="debugging-a-user-control"></a>ユーザー コントロールのデバッグ  
 ユーザー コントロールをデバッグするには、ユーザー コントロールが、SharePoint プロジェクトのアプリケーション ページまたは Web パーツに含まれることを確認します。 Visual Studio プロジェクト内のコードをデバッグする場合と同様、ユーザー コントロール内のコードをデバッグできます。  
  
 Visual Studio デバッガーを開始すると、SharePoint サイトが開きます。  
  
 SharePoint では、ユーザー コントロールを含むアプリケーション ページを開きます。 ユーザー コントロールが Web パーツに含まれている場合は、sharepoint Web パーツ ページに Web パーツを追加します。  
  
 SharePoint プロジェクトのデバッグの詳細については、次を参照してください。 [SharePoint ソリューションのトラブルシューティング](../sharepoint/troubleshooting-sharepoint-solutions.md)です。  
  
## <a name="related-topics"></a>関連トピック  
  
|タイトル|説明|  
|-----------|-----------------|  
|[方法: SharePoint アプリケーション ページまたは Web パーツのユーザー コントロールを作成する](../sharepoint/how-to-create-a-user-control-for-a-sharepoint-application-page-or-web-part.md)|アプリケーション ページと SharePoint で実行される Web パーツで使用できる、再利用可能なカスタム コントロールを作成する方法を示します。|  
  
  