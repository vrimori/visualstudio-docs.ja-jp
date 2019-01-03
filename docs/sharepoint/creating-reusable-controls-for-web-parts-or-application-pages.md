---
title: Web パーツまたはアプリケーション ページの再利用可能なコントロールの作成 |Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
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
ms.openlocfilehash: 7d042c42bae59c6dbf92f0e381444cc011b40db0
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53842824"
---
# <a name="create-reusable-controls-for-web-parts-or-application-pages"></a>Web パーツまたはアプリケーション ページの再利用可能なコントロールを作成します。
  Visual Studio では、アプリケーション ページと SharePoint で実行される Web パーツで使用できる、再利用可能なカスタム コントロールを作成できます。 これらのコントロールは、ユーザー コントロールと呼ばれます。 ユーザー コントロールは、ある種の複合コントロールは ASP.NET Web ページのように動作する、ユーザー コントロールに既存の Web サーバー コントロールとマークアップを追加し、コントロールのプロパティとメソッドを定義できます。 単位として施すの ASP.NET Web ページで、埋め込むことができます。  
  
## <a name="create-a-user-control"></a>ユーザー コントロールを作成します。
 ユーザー コントロールを作成するには、追加、**ユーザー コントロール**を**空の SharePoint プロジェクト**します。 詳細については、「[方法 :SharePoint アプリケーション ページまたは web パーツのユーザー コントロールを作成](../sharepoint/how-to-create-a-user-control-for-a-sharepoint-application-page-or-web-part.md)です。  
  
 追加すると、**ユーザー コントロール**項目、Visual Studio は、プロジェクトのフォルダーが作成され、フォルダーに複数のファイルを追加します。 各ファイルの説明を次の表に示します。  
  
|ファイル|説明|  
|----------|-----------------|  
|ユーザー コントロール ファイル|ユーザー コントロールを定義します。 このファイルにコントロールとマークアップを追加することでユーザー コントロールをデザインします。|  
|コード ファイル|ユーザー コントロールの分離コードが含まれています。 このファイルにイベントを処理するコードを追加します。|  
|デザイナー コード ファイル|デザイナーによって生成されたコードが含まれ、直接編集する必要がありますはありません。|  
  
## <a name="design-the-user-control"></a>ユーザー コントロールのデザイン
 Visual Studio で Visual Web Developer デザイナーを使用して、ユーザー コントロールをデザインします。 プロジェクトでユーザー コントロール ファイルを開いて選択すると、このデザイナーが表示されます、**デザイン**タブ。  

## <a name="consume-the-user-control"></a>ユーザー コントロールを使用します。
 SharePoint では、アプリケーション ページまたは Web パーツに含めるまで、ユーザー コントロールは表示されません。  
  
 ユーザー コントロールをアプリケーション ページに含めるには、ASP.NET ユーザー コントロールを追加する Web ページを開きます。 [デザイン] ビューに切り替えるソリューション エクスプ ローラーで、カスタム ユーザー コントロール ファイルを選択し、ページにドラッグします。 ASP.NET ユーザー コントロールがページに追加され、デザイナーは、ページをユーザー コントロールを認識するのに必要な @ Register ディレクティブを作成します。 コントロールのパブリック プロパティおよびメソッドで処理することができます。  
  
 ユーザー コントロールを Web パーツに含めるには、Web パーツに、ユーザー コントロールを追加<xref:System.Web.UI.WebControls.WebParts.Part.Controls%2A>Web パーツ コード ファイル内のコレクション。 次の例では、ユーザー コントロールを<xref:System.Web.UI.WebControls.WebParts.Part.Controls%2A>Web パーツのコレクション。  
  
 [!code-vb[SP_VisualWebPart#5](../sharepoint/codesnippet/VisualBasic/sp_visualwebpart.vb/visualwebpart1/visualwebpart1.vb#5)]
 [!code-csharp[SP_VisualWebPart#5](../sharepoint/codesnippet/CSharp/sp_visualwebpart.cs/visualwebpart1/visualwebpart1.cs#5)]  
  
## <a name="debug-a-user-control"></a>ユーザー コントロールをデバッグします。
 ユーザー コントロールをデバッグするには、SharePoint プロジェクトで、アプリケーション ページや Web パーツにユーザー コントロールが含まれることを確認します。 Visual Studio プロジェクト内のコードをデバッグする場合と同様に、ユーザー コントロールでコードをデバッグできます。  
  
 Visual Studio デバッガーを開始すると、SharePoint サイトが開きます。  
  
 SharePoint では、ユーザー コントロールを含むアプリケーション ページを開きます。 ユーザー コントロールが Web パーツに含まれる場合は、sharepoint Web パーツ ページに Web パーツを追加します。  
  
 SharePoint プロジェクトのデバッグの詳細については、次を参照してください。[のトラブルシューティングを行う SharePoint ソリューション](../sharepoint/troubleshooting-sharepoint-solutions.md)します。  
  
## <a name="related-topics"></a>関連トピック
  
|タイトル|説明|  
|-----------|-----------------|  
|[方法: SharePoint アプリケーション ページまたは web パーツのユーザー コントロールを作成します。](../sharepoint/how-to-create-a-user-control-for-a-sharepoint-application-page-or-web-part.md)|アプリケーション ページと SharePoint で実行される Web パーツで使用できる、再利用可能なカスタム コントロールを作成する方法を示します。|  
