---
title: Web パーツまたはアプリケーション ページの再利用可能なコントロールの作成 |Microsoft ドキュメント
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
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
manager: douge
ms.workload:
- office
ms.openlocfilehash: 47a519db245e2ec15548ba1d46a583d0a73f466f
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/01/2018
ms.locfileid: "34693485"
---
# <a name="creating-reusable-controls-for-web-parts-or-application-pages"></a>Web パーツまたはアプリケーション ページの再利用可能なコントロールを作成します。
  Visual Studio で、アプリケーション ページと SharePoint で実行される Web パーツで使用できる、再利用可能なカスタム コントロールを作成することができます。 これらのコントロールは、ユーザー コントロールと呼ばれます。 ユーザー コントロールは、ASP.NET Web ページと同様に動作する複合コントロールの種類: ユーザー コントロールを既存の Web サーバー コントロールとマークアップを追加し、コントロールのプロパティとメソッドを定義できます。 ASP.NET Web ページで、場所、単位として機能し、埋め込むことができます。  
  
## <a name="create-a-user-control"></a>ユーザー コントロールを作成します。
 ユーザー コントロールを作成するには追加、**ユーザー コントロール**を**空の SharePoint プロジェクト**です。 詳細については、次を参照してください。[する方法: SharePoint アプリケーション ページや Web パーツのユーザー コントロールを作成](../sharepoint/how-to-create-a-user-control-for-a-sharepoint-application-page-or-web-part.md)です。  
  
 追加すると、**ユーザー コントロール**項目、Visual Studio は、プロジェクトのフォルダーが作成され、フォルダーにいくつかのファイルを追加します。 各ファイルの説明を次の表に示します。  
  
|ファイル|説明|  
|----------|-----------------|  
|ユーザー コントロール ファイル|ユーザー コントロールを定義します。 このファイルへのコントロールとマークアップを追加することでユーザー コントロールをデザインします。|  
|コード ファイル|ユーザー コントロールの分離コードが含まれています。 このファイルにイベントを処理するコードを追加します。|  
|デザイナー コード ファイル|デザイナーによって生成されたコードが含まれており、直接を編集しないでください。|  
  
## <a name="design-the-user-control"></a>ユーザー コントロールをデザインします。
 Visual Studio で Visual Web Developer デザイナーを使用してユーザー コントロールをデザインします。 プロジェクトのユーザー コントロール ファイルを開きますを選択すると、このデザイナーが表示されます、**デザイン**タブです。  

## <a name="consume-the-user-control"></a>ユーザー コントロールを使用します。
 SharePoint では、アプリケーション ページまたは Web パーツに含まれるまで、ユーザー コントロールは表示されません。  
  
 アプリケーション ページで、ユーザー コントロールを含めるには、ASP.NET ユーザー コントロールを追加する Web ページを開きます。 デザイン ビューに切り替えます、ソリューション エクスプ ローラーで、カスタム ユーザー コントロール ファイルを選択し、ページにドラッグします。 ASP.NET ユーザー コントロールがページに追加し、デザイナーは、ユーザー コントロールを認識するように、ページに必要な @ Register ディレクティブを作成します。 コントロールのパブリック プロパティとメソッドを使用できますようになりました。  
  
 Web パーツのユーザー コントロールを含めるには、Web パーツにユーザー コントロールを追加<xref:System.Web.UI.WebControls.WebParts.Part.Controls%2A>Web パーツ コード ファイル内のコレクション。 次の例では、ユーザー コントロールを<xref:System.Web.UI.WebControls.WebParts.Part.Controls%2A>Web パーツのコレクション。  
  
 [!code-vb[SP_VisualWebPart#5](../sharepoint/codesnippet/VisualBasic/sp_visualwebpart.vb/visualwebpart1/visualwebpart1.vb#5)]
 [!code-csharp[SP_VisualWebPart#5](../sharepoint/codesnippet/CSharp/sp_visualwebpart.cs/visualwebpart1/visualwebpart1.cs#5)]  
  
## <a name="debug-a-user-control"></a>ユーザー コントロールをデバッグします。
 ユーザー コントロールをデバッグするには、ユーザー コントロールが、SharePoint プロジェクトのアプリケーション ページまたは Web パーツに含まれることを確認します。 Visual Studio プロジェクト内のコードをデバッグする場合と同様、ユーザー コントロール内のコードをデバッグできます。  
  
 Visual Studio デバッガーを開始すると、SharePoint サイトが開きます。  
  
 SharePoint では、ユーザー コントロールを含むアプリケーション ページを開きます。 ユーザー コントロールが Web パーツに含まれている場合は、sharepoint Web パーツ ページに Web パーツを追加します。  
  
 SharePoint プロジェクトのデバッグの詳細については、次を参照してください。 [SharePoint ソリューションのトラブルシューティング](../sharepoint/troubleshooting-sharepoint-solutions.md)です。  
  
## <a name="related-topics"></a>関連トピック
  
|タイトル|説明|  
|-----------|-----------------|  
|[方法: SharePoint アプリケーション ページまたは Web パーツのユーザー コントロールを作成する](../sharepoint/how-to-create-a-user-control-for-a-sharepoint-application-page-or-web-part.md)|アプリケーション ページと SharePoint で実行される Web パーツで使用できる、再利用可能なカスタム コントロールを作成する方法を示します。|  
  