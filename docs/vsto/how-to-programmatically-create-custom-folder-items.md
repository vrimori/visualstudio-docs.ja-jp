---
title: "方法: プログラムによってカスタム フォルダーのアイテムを作成 |Microsoft ドキュメント"
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
- Outlook folders [Office development in Visual Studio], creating
- Outlook folders [Office development in Visual Studio], custom
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 8b8b5dd6a287f5e6daf6391e77baeee8da8f129d
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-programmatically-create-custom-folder-items"></a>方法: プログラムによってカスタム フォルダーのアイテムを作成する
  この例では、Microsoft Office Outlook で新しいフォルダーを作成します。 ログオンしたユーザーの名前は、フォルダー名に使用されます。  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="example"></a>例  
 [!code-csharp[Trin_OL_CustFolderItem#1](../vsto/codesnippet/CSharp/Trin_OL_CustFolderItem/thisaddin.cs#1)]  
  
## <a name="see-also"></a>参照  
 [フォルダーの操作](../vsto/working-with-folders.md)   
 [方法: プログラムによって Outlook の連絡先にエントリを追加](../vsto/how-to-programmatically-add-an-entry-to-outlook-contacts.md)   
 [方法: プログラムによって予定を作成する](../vsto/how-to-programmatically-create-appointments.md)  
  
  