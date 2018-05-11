---
title: '方法: プログラムによって電子メールを送信 |Microsoft ドキュメント'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- mail items [Office development in Visual Studio], sending e-mail
- Outlook [Office development in Visual Studio], creating e-mail
- Outlook [Office development in Visual Studio], sending e-mail
- e-mail [Office development in Visual Studio], sending
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: c3ee656a8a4965f01969bad19d66d0ea6215bcbe
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-programmatically-send-e-mail"></a>方法: プログラムによって電子メールを送信  
  この例は、ドメイン名が設定されている連絡先に電子メール メッセージを送信**example.com**が電子メール アドレス。  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="example"></a>例  
 [!code-csharp[Trin_OL_ProgramEmail#1](../vsto/codesnippet/CSharp/Trin_OL_ProgramEMail/thisaddin.cs#1)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 この例で必要な要素は次のとおりです。  
  
-   ドメイン名を持つ連絡先**example.com**が電子メール アドレス。  
  
## <a name="robust-programming"></a>信頼性の高いプログラミング  
 ドメイン名を検索するフィルターのコードを削除しないで**example.com**です。ソリューションが、フィルターを削除する場合は、すべての連絡先に電子メール メッセージを送信します。  
  
## <a name="see-also"></a>関連項目  
 [メール アイテムの操作](../vsto/working-with-mail-items.md)   
 [方法: プログラムによって電子メール アイテムを作成します。](../vsto/how-to-programmatically-create-an-e-mail-item.md)   
 [方法: プログラムによって Outlook の連絡先にアクセス](../vsto/how-to-programmatically-access-outlook-contacts.md)   
 [方法: プログラムによって電子メール メッセージを受信したときにアクションを実行する](../vsto/how-to-programmatically-perform-actions-when-an-e-mail-message-is-received.md)  
  
  