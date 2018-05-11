---
title: フォーム領域の Outlook でのカスタム アクション |Microsoft ドキュメント
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- form regions [Office development in Visual Studio], custom actions
- custom actions [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 1e81528aa5008b7d6f78f560d0bc0139a1e0799a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="custom-actions-in-outlook-form-regions"></a>Outlook フォーム領域のカスタム動作
  アクションは、Microsoft Office Outlook アイテムに応答するユーザーを有効にするボタンを表示します。 たとえば、メール アイテムに応答して、ユーザーをクリックして、**返信**、**全員に返信**、または**フォワード**アクション ボタン。 これらの各アクションは、新しいメール アイテムを作成し、元の項目から情報を使用して、項目のフィールドを追加します。  
  
 Outlook アイテムの任意の種類を開くカスタム動作を作成することができます。 たとえば、新しい予定またはタスク項目を開くカスタム アクションを追加することができます。 カスタム アクションのプロパティを設定またはカスタム コードを使用して、新しい項目のフィールドに設定します。 カスタム アクションに表示されます、**カスタム動作**Outlook インスペクター ウィンドウで開かれている項目のドロップダウンします。  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="adding-custom-actions-to-a-form-region"></a>フォーム領域へのカスタム アクションの追加  
 フォーム領域に、カスタム アクションを追加するには、使用、**カスタム アクション** ダイアログ ボックス。 開くことができます、**カスタム動作** ダイアログ ボックスで**ソリューション エクスプ ローラー**を展開して、**マニフェスト** ノードを選択すると、 **CustomActions**プロパティ、および省略記号ボタンをクリックし (![ASP.NET モバイル デザイナー楕円](../sharepoint/media/mwellipsis.gif "ASP.NET モバイル デザイナー楕円"))。  
  
 使用することができます、**カスタム動作** ダイアログ ボックスを指定する、*フォームのターゲット*です。 ターゲット フォームは、ユーザーがカスタム アクションを実行するときに表示されるフォームです。  
  
 使用することも、**カスタム動作**ダイアログ ボックスについては、元の項目を対象のフォームに表示する方法を指定します。  
  
 次の表で使用可能なプロパティ、**カスタム動作** ダイアログ ボックス。  
  
|プロパティ|説明|  
|--------------|-----------------|  
|**AddressLike**|ターゲットの形式のアドレスを指定する方法を指定します。|  
|**本文**|元のアイテムの本文をターゲット フォームに追加する方法を指定します。|  
|**有効**|カスタム アクションが有効になっているかどうかを示します。 このプロパティ設定されている場合**false**、カスタム アクションは実行できません。|  
|**メソッド**|カスタム アクションを実行すると、利用可能な応答の種類を指定します。 カスタム アクションでは、フォームを送信、フォームを開く、またはユーザーに確認を送信するか、フォームを開いているかどうかできます。|  
|**Name**|コードでこのカスタム アクションを参照に使用できる内部名を指定します。|  
|**ShowOnRibbon**|元のアイテムのリボンにカスタム動作を表示するかどうかを示します。|  
|**SubjectPrefix**|ターゲットの形式の件名行の先頭に挿入する文字列を指定します。|  
|**TargetForm**|ターゲットの形式のメッセージ クラス名を指定します。 たとえば、「 **IPM です。タスク**タスク フォームを開きます。|  
|**タイトル**|カスタム アクション ボタンのラベルを指定します。|  
  
## <a name="customizing-a-custom-action-at-run-time"></a>実行時にカスタム動作のカスタマイズ  
 コードを使用して、カスタム動作を動作を追加することもできます。 たとえばは電子メールの受信者の名前を取得し、新しい予定アイテムの参加者としてそれらの名前を追加するコードを追加することができます。 これを行うには、処理、 [CustomAction](http://msdn.microsoft.com/library/office/ff862186.aspx)のイベント、 [MailItem オブジェクト](http://msdn.microsoft.com/library/office/ff861332.aspx)です。  
  
## <a name="see-also"></a>関連項目  
 [Outlook フォーム領域の作成](../vsto/creating-outlook-form-regions.md)   
 [チュートリアル: Outlook フォーム領域のデザイン](../vsto/walkthrough-designing-an-outlook-form-region.md)   
 [フォーム領域の Outlook メッセージ クラスへの関連付け](../vsto/associating-a-form-region-with-an-outlook-message-class.md)  
  
  