---
title: "方法: プログラムによって連絡先の電子メール アドレスの検索 |Microsoft ドキュメント"
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
helpviewer_keywords:
- e-mail [Office development in Visual Studio], searching
- contacts [Office development in Visual Studio], searching
- searching contacts
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: d9ab451d433536c7ebf5931aa2c971b08ed5c09b
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-programmatically-search-for-an-e-mail-address-in-contacts"></a>方法: プログラムによって連絡先から電子メール アドレスを検索する
  この例では、連絡先フォルダーから、電子メール アドレスに **example.com** というドメイン名が含まれている連絡先を検索します。  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="example"></a>例  
 [!code-csharp[Trin_OL_SearchEmail#1](../vsto/codesnippet/CSharp/Trin_OL_SearchEmail/thisaddin.cs#1)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 この例で必要な要素は次のとおりです。  
  
-   電子メール アドレスに **example.com** というドメイン名が含まれており (たとえば、 `somebody@example.com`)、姓と名が設定されている連絡先。  
  
## <a name="see-also"></a>参照  
 [連絡先アイテムの操作](../vsto/working-with-contact-items.md)   
 [方法: プログラムによって電子メールを送信](../vsto/how-to-programmatically-send-e-mail-programmatically.md)   
 [方法: プログラムによって Outlook の連絡先にアクセス](../vsto/how-to-programmatically-access-outlook-contacts.md)   
 [方法: プログラムによって Outlook の連絡先にエントリを追加する](../vsto/how-to-programmatically-add-an-entry-to-outlook-contacts.md)  
  
  