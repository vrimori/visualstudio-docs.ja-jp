---
title: Outlook オブジェクト モデルの概要
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VST.ProjectItem.OutlookAddin
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Outlook [Office development in Visual Studio], object model overview
- object models [Office development in Visual Studio], Office
- objects [Office development in Visual Studio], Office object models
- object models [Office development in Visual Studio], Outlook
- Office object models
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: b11757990a17a867776376454142e5b84ee82510
ms.sourcegitcommit: 96a6d1f16d06ca28d309d05b6e9fbd52f628cdbc
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/09/2018
ms.locfileid: "40008269"
---
# <a name="outlook-object-model-overview"></a>Outlook オブジェクト モデルの概要
  Microsoft Office Outlook 用の VSTO アドインを開発するには、Outlook オブジェクト モデルによって提供されるオブジェクトとのやり取りが可能です。 Outlook オブジェクト モデルは、ユーザー インターフェイスで項目を表すクラスとインターフェイスを提供します。 たとえば、<xref:Microsoft.Office.Interop.Outlook.Application> オブジェクトは、アプリケーション全体を表し、<xref:Microsoft.Office.Interop.Outlook.Folder> オブジェクトは、電子メール メッセージや他のアイテムを含むフォルダーを表します。<xref:Microsoft.Office.Interop.Outlook.MailItem> オブジェクトは、電子メール メッセージを表します。  
  
 このトピックでは、Outlook オブジェクト モデルのいくつかの主要なオブジェクトの概要を簡単に説明します。 全体の Outlook オブジェクト モデルの詳細を説明できます資料については、次を参照してください。 [Outlook オブジェクト モデルのドキュメントを使用して、](#refdoc)します。  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
 ![ビデオへのリンク](../vsto/media/playvideo.gif "ビデオへのリンク")関連するビデオ デモについては、次を参照してください。[方法: Outlook のカスタム タスク レポートの作成を使用しますか?](http://go.microsoft.com/fwlink/?LinkID=130315)します。  
  
## <a name="access-objects-in-an-outlook-project"></a>Outlook プロジェクトでオブジェクトにアクセス  
 Outlook では、多くのオブジェクトが操作対象になります。 オブジェクト モデルを効果的に使用するには、次の最上位レベルのオブジェクトについて理解する必要があります。  
  
-   <xref:Microsoft.Office.Interop.Outlook.Application>  
  
-   <xref:Microsoft.Office.Interop.Outlook.Explorer>  
  
-   <xref:Microsoft.Office.Interop.Outlook.Inspector>  
  
-   <xref:Microsoft.Office.Interop.Outlook.Folder>  
  
-   <xref:Microsoft.Office.Interop.Outlook.MailItem>  
  
-   <xref:Microsoft.Office.Interop.Outlook.AppointmentItem>  
  
-   <xref:Microsoft.Office.Interop.Outlook.TaskItem>  
  
-   <xref:Microsoft.Office.Interop.Outlook.ContactItem>  
  
### <a name="application-object"></a>Application オブジェクト  
 <xref:Microsoft.Office.Interop.Outlook.Application> オブジェクトは Outlook のアプリケーションを表し、Outlook オブジェクト モデルで最上位レベルのオブジェクトです。 このオブジェクトの最も重要なメンバーには、次のようなものがあります。  
  
-   [CreateItem](/previous-versions/office/developer/office-2003/aa220082(v=office.11))メソッド、電子メール メッセージ、タスク、または予定などの新しい項目の作成に使用できます。  
  
-   <xref:Microsoft.Office.Interop.Outlook._Application.Explorers%2A> プロパティ。これを使用して、Outlook のユーザー インターフェイス (UI) で、フォルダーの内容を表示するウィンドウにアクセスできます。  
  
-   <xref:Microsoft.Office.Interop.Outlook._Application.Inspectors%2A> プロパティ。これを使用して、電子メール メッセージや会議出席依頼などの単一の項目の内容を表示するウィンドウにアクセスできます。  
  
 インスタンスを取得する、<xref:Microsoft.Office.Interop.Outlook.Application>オブジェクトでのアプリケーションのフィールドを使用して、`ThisAddIn`プロジェクト内のクラス。 詳細については、次を参照してください。[プログラム VSTO アドイン](../vsto/programming-vsto-add-ins.md)します。  
  
> [!NOTE]  
>  プロパティと Outlook オブジェクト モデルの保護によってブロックされているメソッドを使用する場合は、セキュリティの警告を回避するためには、[アプリケーション] フィールドから Outlook オブジェクトを取得、`ThisAddIn`クラス。 詳細については、次を参照してください。 [Office ソリューションの特定のセキュリティに関する考慮事項](../vsto/specific-security-considerations-for-office-solutions.md)します。  
  
### <a name="explorer-object"></a>エクスプ ローラー オブジェクト  
 <xref:Microsoft.Office.Interop.Outlook.Explorer> オブジェクトは、電子メール メッセージ、タスク、または予定などの項目を含むフォルダーの内容を表示するウィンドウを表します。 <xref:Microsoft.Office.Interop.Outlook.Explorer> オブジェクトには、ウィンドウを変更するために使用するメソッドとプロパティ、およびウィンドウが変更されたときに発生するイベントが含まれます。  
  
 <xref:Microsoft.Office.Interop.Outlook.Explorer> オブジェクトを取得するには、以下のいずれかを実行します。  
  
-   <xref:Microsoft.Office.Interop.Outlook._Application.Explorers%2A> オブジェクトの <xref:Microsoft.Office.Interop.Outlook.Application> プロパティを使用して、Outlook 内のすべての <xref:Microsoft.Office.Interop.Outlook.Explorer> オブジェクトにアクセスします。  
  
-   <xref:Microsoft.Office.Interop.Outlook.Application> オブジェクトの <xref:Microsoft.Office.Interop.Outlook._Application.ActiveExplorer%2A> メソッドを使用して、現在フォーカスしている <xref:Microsoft.Office.Interop.Outlook.Explorer> を取得します。  
  
-   <xref:Microsoft.Office.Interop.Outlook.Folder> オブジェクトの `GetExplorer` メソッドを使用して、現在のフォルダーの <xref:Microsoft.Office.Interop.Outlook.Explorer> を取得します。  
  
### <a name="inspector-object"></a>Inspector オブジェクト  
 <xref:Microsoft.Office.Interop.Outlook.Inspector> オブジェクトは、電子メール メッセージ、タスク、または予定などの単一の項目を表示するウィンドウを表します。 <xref:Microsoft.Office.Interop.Outlook.Inspector> オブジェクトには、ウィンドウを変更するために使用するメソッドとプロパティ、およびウィンドウが変更されたときに発生するイベントが含まれます。  
  
 <xref:Microsoft.Office.Interop.Outlook.Inspector> オブジェクトを取得するには、以下のいずれかを実行します。  
  
-   <xref:Microsoft.Office.Interop.Outlook._Application.Inspectors%2A> オブジェクトの <xref:Microsoft.Office.Interop.Outlook.Application> プロパティを使用して、Outlook 内のすべての <xref:Microsoft.Office.Interop.Outlook.Inspector> オブジェクトにアクセスします。  
  
-   <xref:Microsoft.Office.Interop.Outlook._Application.ActiveInspector%2A> オブジェクトの <xref:Microsoft.Office.Interop.Outlook.Application> メソッドを使用して、現在フォーカスしている <xref:Microsoft.Office.Interop.Outlook.Inspector> を取得します。  
  
-   特定の項目 (<xref:Microsoft.Office.Interop.Outlook.MailItem> や <xref:Microsoft.Office.Interop.Outlook.AppointmentItem> など) の `GetInspector` メソッドを使用して、それらの項目に関連付けられているインスペクタを取得します。  
  
### <a name="folder-object"></a>フォルダーのオブジェクト  
 <xref:Microsoft.Office.Interop.Outlook.Folder> オブジェクトは、電子メール メッセージ、連絡先、タスク、およびその他の項目が含まれているフォルダーを表します。 Outlook には 16 の既定の <xref:Microsoft.Office.Interop.Outlook.Folder> オブジェクトが用意されています。  
  
 既定の <xref:Microsoft.Office.Interop.Outlook.Folder> オブジェクトは <xref:Microsoft.Office.Interop.Outlook.OlDefaultFolders> 列挙値により、定義されます。 たとえば、オブジェクトに適用された  
  
 Microsoft.Office.Interop.Outlook.OlDefaultFolders.olFolderInbox に対応する、**受信トレイ**Outlook のフォルダー。  
  
 既定値にアクセスする方法を示す例については<xref:Microsoft.Office.Interop.Outlook.Folder>され、新しい作成<xref:Microsoft.Office.Interop.Outlook.Folder>を参照してください[方法: プログラムによってカスタム フォルダーのアイテムを作成](../vsto/how-to-programmatically-create-custom-folder-items.md)です。  
  
### <a name="mailitem-object"></a>MailItem オブジェクト  
 <xref:Microsoft.Office.Interop.Outlook.MailItem> オブジェクトは電子メール メッセージを表します。 <xref:Microsoft.Office.Interop.Outlook.MailItem> オブジェクトは通常、「 **受信トレイ**」、「 **送信済みアイテム**」、および「 **送信トレイ**」などのフォルダーにあります。 <xref:Microsoft.Office.Interop.Outlook.MailItem> は、電子メール メッセージを作成し、送信するために使用できるプロパティとメソッドを公開します。  
  
 電子メール メッセージを作成する方法を示しますたとえば、次を参照してください。[方法: プログラムによって電子メール アイテムを作成](../vsto/how-to-programmatically-create-an-e-mail-item.md)です。  
  
### <a name="appointmentitem-object"></a>AppointmentItem オブジェクト  
 <xref:Microsoft.Office.Interop.Outlook.AppointmentItem> オブジェクトは **カレンダー** フォルダー内の会議、1 回限りの予定、または定期的な予定や会議を表します。 <xref:Microsoft.Office.Interop.Outlook.AppointmentItem> オブジェクトには、会議出席依頼の応答や転送などのアクションを実行するメソッドと、会議の場所や時間など、会議詳細を指定するプロパティが含まれます。  
  
 予定を作成する方法の例を参照してください[方法: プログラムによって会議出席依頼を作成](../vsto/how-to-programmatically-create-a-meeting-request.md)です。  
  
### <a name="taskitem-object"></a>TaskItem オブジェクト  
 <xref:Microsoft.Office.Interop.Outlook.TaskItem> オブジェクトは、指定した期間内で実行するタスクを表します。 <xref:Microsoft.Office.Interop.Outlook.TaskItem> オブジェクトは **[タスク]** フォルダーにあります。  
  
 タスクを作成するには使用、 [CreateItem](/previous-versions/office/developer/office-2003/aa220082(v=office.11))のメソッド、<xref:Microsoft.Office.Interop.Outlook.Application>オブジェクトし、値を渡す<xref:Microsoft.Office.Interop.Outlook.OlItemType.olTaskItem>パラメーター。  
  
### <a name="contactitem-object"></a>ContactItem オブジェクト  
 <xref:Microsoft.Office.Interop.Outlook.ContactItem>オブジェクト内の連絡先を表します、**連絡先**フォルダー。 <xref:Microsoft.Office.Interop.Outlook.ContactItem> オブジェクトには、住所、電子メール アドレス、電話番号など、そのオブジェクトが表す人のさまざまな連絡先情報が含まれます。  
  
 新しい連絡先を作成する方法を示しますたとえば、次を参照してください。[方法: プログラムによって Outlook の連絡先にエントリを追加](../vsto/how-to-programmatically-add-an-entry-to-outlook-contacts.md)します。 既存の連絡先を検索する方法を示しますたとえば、次を参照してください。[方法: プログラムによって特定の連絡先を検索](../vsto/how-to-programmatically-search-for-a-specific-contact.md)します。  
  
##  <a name="refdoc"></a> Outlook オブジェクト モデル ドキュメントを使用します。  
 Outlook オブジェクト モデルに関する詳細については、Outlook プライマリ相互運用機能アセンブリ (PIA) のリファレンスと、VBA オブジェクト モデルのリファレンスを参照してください。  
  
### <a name="primary-interop-assembly-reference"></a>プライマリ相互運用機能アセンブリのリファレンス  
 Outlook の PIA リファレンスには、Outlook 2010 のプライマリ相互運用機能アセンブリの種類について記述されています。 詳細については、次を参照してください。 [Outlook 2010 プライマリ相互運用機能アセンブリ リファレンス](http://go.microsoft.com/fwlink/?LinkId=189580)します。  
  
 この資料には、PIA の型すべての情報を提供されています。さらに、PAI の構造に関する詳細情報と、一般的な Outlook 自動化タスクのコード例も提供されています。  
  
### <a name="vba-object-model-reference"></a>VBA オブジェクト モデル リファレンス  
 VBA オブジェクト モデルのリファレンスでは、Visual Basic for Applications (VBA) コードに公開される Outlook オブジェクト モデルについて説明しています。 詳細については、次を参照してください。 [Outlook 2010 オブジェクト モデル リファレンス](http://go.microsoft.com/fwlink/?LinkId=199769)します。  
  
 VBA オブジェクト モデルのリファレンス内のオブジェクトとメンバーはすべて、Outlook PIA の型とメンバーに対応します。 たとえば、オブジェクト インスペクターを VBA オブジェクト モデルのリファレンス内の対応する、 <xref:Microsoft.Office.Interop.Outlook.Inspector> Outlook pia オブジェクト。 VBA オブジェクト モデルのリファレンスでは、ほとんどのプロパティ、メソッド、およびイベントのコード例を紹介しています。ただし、Visual Studio を使用して作成した Outlook VSTO アドイン プロジェクトでこのリファレンス内の VBA コードを使用するには、それらを Visual Basic または Visual C# に変換する必要があります。  
  
### <a name="related-topics"></a>関連トピック  
  
|タイトル|説明|  
|-----------|-----------------|  
|[連絡先項目を操作します。](../vsto/working-with-contact-items.md)|アドレス帳を使用したさまざまなタスクを実行する方法を説明するトピックを提供します。|  
|[メールの項目を操作します。](../vsto/working-with-mail-items.md)|メール アイテムを使用してタスクを実行する方法を説明するトピックを提供します。|  
|[フォルダーを操作します。](../vsto/working-with-folders.md)|フォルダーを使用してタスクを実行する方法を説明するトピックを提供します。|  
|[予定表項目を操作します。](../vsto/working-with-calendar-items.md)|予定表アイテムを使用してタスクを実行する方法を説明するトピックを提供します。|  
|[方法: プログラムによって現在の Outlook アイテムを確認します。](../vsto/how-to-programmatically-determine-the-current-outlook-item.md)|現在のフォルダー名と、選択したアイテムに関する情報を表示する方法を示します。|  
  