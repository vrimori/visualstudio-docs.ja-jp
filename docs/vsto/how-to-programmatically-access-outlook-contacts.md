---
title: "方法: プログラムによって Outlook の連絡先にアクセス |Microsoft ドキュメント"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- contacts [Office development in Visual Studio], searching
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload:
- office
ms.openlocfilehash: 4d4d88416507f7e63cd112df350dc93b2e13605f
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-programmatically-access-outlook-contacts"></a>方法: プログラムによって Outlook の連絡先にアクセスする
  この例では、最後の名前が指定した検索文字列を含むすべての連絡先を検索します。  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="example"></a>例  
 [!code-csharp[Trin_OL_AccessContacts#1](../vsto/codesnippet/CSharp/Trin_OL_AccessContacts.trin_ol_accesscontacts/thisaddin.cs#1)]
 [!code-csharp[Trin_OL_AccessContacts#1](../vsto/codesnippet/CSharp/Trin_OL_AccessContacts.trin_ol_accesscontacts/thisaddin.cs#1)]
 [!code-vb[Trin_OL_AccessContacts#1](../vsto/codesnippet/VisualBasic/Trin_OL_AccessContacts/thisaddin.vb#1)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 この例で必要な要素は次のとおりです。  
  
-   連絡先の姓を含む文字列"**Na"** (たとえば、Tzipi Butnaru) で、**連絡先**フォルダーです。  
  
## <a name="see-also"></a>参照  
 [連絡先アイテムの操作](../vsto/working-with-contact-items.md)   
 [方法: プログラムによって Outlook の連絡先にエントリを追加](../vsto/how-to-programmatically-add-an-entry-to-outlook-contacts.md)   
 [方法: プログラムによって特定の連絡先の検索](../vsto/how-to-programmatically-search-for-a-specific-contact.md)   
 [方法: プログラムによって連絡先の電子メール アドレスの検索](../vsto/how-to-programmatically-search-for-an-e-mail-address-in-contacts.md)   
 [方法: プログラムによって Outlook の連絡先を削除する](../vsto/how-to-programmatically-delete-outlook-contacts.md)  
  
  