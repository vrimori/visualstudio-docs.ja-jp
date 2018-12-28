---
title: Outlook フォーム領域のカスタム アクション
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
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: 6b19b65c387e4ffc59108be71c143f130b347551
ms.sourcegitcommit: a715de2ba8c703f37aa2102567b1aa2c0f05a117
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/15/2018
ms.locfileid: "53441661"
---
# <a name="custom-actions-in-outlook-form-regions"></a>Outlook フォーム領域のカスタム アクション
  アクションは、Microsoft Office Outlook アイテムに応答するユーザーを有効にするボタンを表示します。 たとえば、メール アイテムに応答するユーザー クリックして、**応答**、**全員へ返信**、または**フォワード**アクション ボタン。 これらの各アクションは、新しいメール アイテムを作成し、元の項目からの情報を使用して項目のフィールドを入力します。  
  
 Outlook アイテムの任意の種類を表示するカスタム アクションを作成できます。 たとえば、新しい予定またはタスク アイテムを開くカスタム アクションを追加できます。 カスタム アクションのプロパティを設定またはカスタム コードを使用して、新しい項目のフィールドに入力します。 カスタム アクションに表示されます、**カスタム アクション**Outlook インスペクター ウィンドウで開いているアイテムのドロップダウン リスト。  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="add-custom-actions-to-a-form-region"></a>フォーム領域にカスタム アクションを追加します。  
 フォーム領域には、カスタム アクションを追加するには、使用、**カスタム アクション** ダイアログ ボックス。 開くことができます、**カスタム アクション** ダイアログ ボックスで**ソリューション エクスプ ローラー**を展開して、**マニフェスト**ノードを選択すると、 **CustomActions**プロパティ、および、省略記号ボタンをクリックし (![ASP.NET モバイル デザイナー楕円](../sharepoint/media/mwellipsis.gif "ASP.NET モバイル デザイナー楕円"))。  
  
 使用することができます、**カスタム アクション**を指定する ダイアログ ボックス、*対象フォーム*します。 ターゲット フォームは、ユーザーがカスタム アクションを実行するときに表示されるフォームです。  
  
 使用することも、**カスタム アクション**ダイアログ ボックスに表示されるターゲット フォームの元の項目からの情報を表示する方法を指定します。  
  
 次の表に、プロパティで使用できる、**カスタム アクション** ダイアログ ボックス。  
  
|プロパティ|説明|  
|--------------|-----------------|  
|**AddressLike**|ターゲット フォームのアドレスを指定する方法を指定します。|  
|**本文**|ターゲット フォームに、元の項目の本文を追加する方法を指定します。|  
|**有効**|カスタム アクションが有効になっているかどうかを示します。 このプロパティ設定されている場合**false**、カスタム アクションが無効になっています。|  
|**メソッド**|カスタム アクションを実行すると、使用可能な応答の種類を指定します。 カスタムのアクションでは、フォームを送信、フォームを開く、または送信や、フォームを開くかどうかを求めることができます。|  
|**Name**|コードでこのカスタム アクションを参照するために使用できる内部名を指定します。|  
|**ShowOnRibbon**|元のアイテムのリボンにカスタム アクションを表示するかどうかを示します。|  
|**SubjectPrefix**|ターゲット フォームの件名行の先頭に挿入する文字列を指定します。|  
|**TargetForm**|ターゲット フォームのメッセージ クラス名を指定します。 たとえば、「 **IPM します。タスク**タスク フォームが開きます。|  
|**タイトル**|カスタム アクション ボタンのラベルを指定します。|  
  
## <a name="customize-a-custom-action-at-runtime"></a>実行時にカスタム動作をカスタマイズします。  
 コードを使用して、カスタム アクションに動作を追加することもできます。 たとえば、電子メール受信者の名前を受け取り、新しい予定アイテムの参加者としてこれらの名前を追加するコードを追加できます。 これを行うには、処理、 [CustomAction](/office/vba/api/Outlook.MailItem.CustomAction)のイベント、 [MailItem オブジェクト](/office/vba/api/Outlook.MailItem)します。  
  
## <a name="see-also"></a>関連項目  
 [Outlook フォーム領域を作成します。](../vsto/creating-outlook-form-regions.md)   
 [チュートリアル: Outlook フォーム領域をデザインします。](../vsto/walkthrough-designing-an-outlook-form-region.md)   
 [フォーム領域を Outlook メッセージ クラスに関連付ける](../vsto/associating-a-form-region-with-an-outlook-message-class.md)  
  
  