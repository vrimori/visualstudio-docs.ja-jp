---
title: '方法: プログラムによって連絡先の電子メール アドレスの検索 |Microsoft ドキュメント'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- e-mail [Office development in Visual Studio], searching
- contacts [Office development in Visual Studio], searching
- searching contacts
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 16b79f5f14f1e0d8c5c82a00f5f2ccf2412b991b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-programmatically-search-for-an-e-mail-address-in-contacts"></a>方法: プログラムによって連絡先から電子メール アドレスを検索する
  この例では、連絡先フォルダーから、電子メール アドレスに **example.com** というドメイン名が含まれている連絡先を検索します。  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="example"></a>例  
 [!code-csharp[Trin_OL_SearchEmail#1](../vsto/codesnippet/CSharp/Trin_OL_SearchEmail/thisaddin.cs#1)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 この例で必要な要素は次のとおりです。  
  
-   電子メール アドレスに **example.com** というドメイン名が含まれており (たとえば、 `somebody@example.com`)、姓と名が設定されている連絡先。  
  
## <a name="see-also"></a>関連項目  
 [連絡先アイテムの操作](../vsto/working-with-contact-items.md)   
 [方法: プログラムによって電子メールを送信](../vsto/how-to-programmatically-send-e-mail-programmatically.md)   
 [方法: プログラムによって Outlook の連絡先にアクセス](../vsto/how-to-programmatically-access-outlook-contacts.md)   
 [方法: プログラムによって Outlook の連絡先にエントリを追加する](../vsto/how-to-programmatically-add-an-entry-to-outlook-contacts.md)  
  
  