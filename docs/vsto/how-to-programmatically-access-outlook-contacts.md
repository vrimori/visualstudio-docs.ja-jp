---
title: '方法: プログラムによって Outlook の連絡先へのアクセスします。'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- contacts [Office development in Visual Studio], searching
author: John-Hart
ms.author: johnhart
ms.workload:
- office
ms.openlocfilehash: 79fb7ea0b8f44943b3a8665cb9cf83160e8e0ffe
ms.sourcegitcommit: a205ff1b389fba1803acd32c54df7feb0ef7a203
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/20/2018
ms.locfileid: "53647024"
---
# <a name="how-to-programmatically-access-outlook-contacts"></a>方法: プログラムによって Outlook の連絡先へのアクセスします。
  この例では、最後の名前が指定した検索文字列を含むすべての連絡先を検索します。  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="example"></a>例  
 [!code-csharp[Trin_OL_AccessContacts#1](../vsto/codesnippet/CSharp/Trin_OL_AccessContacts.trin_ol_accesscontacts/thisaddin.cs#1)]
 [!code-csharp[Trin_OL_AccessContacts#1](../vsto/codesnippet/CSharp/Trin_OL_AccessContacts.trin_ol_accesscontacts/thisaddin.cs#1)]
 [!code-vb[Trin_OL_AccessContacts#1](../vsto/codesnippet/VisualBasic/Trin_OL_AccessContacts/thisaddin.vb#1)]  
  
## <a name="compile-the-code"></a>コードのコンパイル  
 この例で必要な要素は次のとおりです。  
  
-   連絡先の姓が文字列を含む"**Na"** (Tzipi Butnaru など) で、**連絡先**フォルダー。  
  
## <a name="see-also"></a>関連項目  
 [連絡先項目を操作します。](../vsto/working-with-contact-items.md)   
 [方法: プログラムによって Outlook の連絡先にエントリを追加します。](../vsto/how-to-programmatically-add-an-entry-to-outlook-contacts.md)   
 [方法: プログラムによって特定の連絡先を検索します。](../vsto/how-to-programmatically-search-for-a-specific-contact.md)   
 [方法: プログラムによって連絡先から電子メール アドレスを検索します。](../vsto/how-to-programmatically-search-for-an-e-mail-address-in-contacts.md)   
 [方法: プログラムによって Outlook の連絡先を削除します。](../vsto/how-to-programmatically-delete-outlook-contacts.md)  
  
  