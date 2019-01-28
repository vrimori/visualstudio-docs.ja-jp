---
title: '方法: プログラムによって電子メールを送信します。'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- mail items [Office development in Visual Studio], sending e-mail
- Outlook [Office development in Visual Studio], creating e-mail
- Outlook [Office development in Visual Studio], sending e-mail
- e-mail [Office development in Visual Studio], sending
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 51546047a12e23c688ccfdfd05aeaa9c2ab89f95
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2019
ms.locfileid: "54866728"
---
# <a name="how-to-programmatically-send-email"></a>方法: プログラムによって電子メールを送信します。  
  この例は、ドメイン名を持つ連絡先に電子メール メッセージを送信**example.com**が電子メール アドレス。  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="example"></a>例  
 [!code-csharp[Trin_OL_ProgramEmail#1](../vsto/codesnippet/CSharp/Trin_OL_ProgramEMail/thisaddin.cs#1)]  
  
## <a name="compile-the-code"></a>コードのコンパイル  
 この例で必要な要素は次のとおりです。  
  
-   ドメイン名を持つ連絡先**example.com**が電子メール アドレス。  
  
## <a name="robust-programming"></a>信頼性の高いプログラミング  
 ドメイン名を検索するフィルターのコードを削除しないで**example.com**します。 ソリューションが、フィルターを削除する場合は、すべての連絡先に電子メール メッセージを送信します。  
  
## <a name="see-also"></a>関連項目  
 [メールの項目を操作します。](../vsto/working-with-mail-items.md)   
 [方法: プログラムによって電子メール アイテムを作成します。](../vsto/how-to-programmatically-create-an-e-mail-item.md)   
 [方法: プログラムによって Outlook の連絡先へのアクセスします。](../vsto/how-to-programmatically-access-outlook-contacts.md)   
 [方法: プログラムで電子メール メッセージを受信したときにアクションを実行します。](../vsto/how-to-programmatically-perform-actions-when-an-e-mail-message-is-received.md)  
