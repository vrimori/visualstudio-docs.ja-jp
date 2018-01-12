---
title: "方法: プログラムによって Web ページを Outlook のフォルダーに関連付ける |Microsoft ドキュメント"
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
- folders [Office development in Visual Studio], Web pages and
- Outlook [Office development in Visual Studio], Web pages attached to folders
- Web pages [Office development in Visual Studio], Outlook folders
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 0fa0ccb3035bc4be8e316c96bd5da8c166dcb4b8
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-programmatically-associate-a-web-page-with-an-outlook-folder"></a>方法: プログラムによって Web ページを Outlook のフォルダーに関連付ける
  この例は、という名前のフォルダーの`HtmlView`Microsoft Office Outlook でします。 フォルダーが存在しない場合、コードは、フォルダーを作成し、Web ページを代入します。 フォルダーが存在する場合、コードは、フォルダーの内容を表示します。  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="example"></a>例  
 [!code-csharp[Trin_OL_HTMLFolder#1](../vsto/codesnippet/CSharp/Trin_OL_HTMLFolder/thisaddin.cs#1)]  
  
## <a name="see-also"></a>参照  
 [フォルダーの操作](../vsto/working-with-folders.md)   
 [方法: プログラムによって名前のフォルダーを取得します。](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)   
 [方法: プログラムによってカスタム フォルダーのアイテムを作成する](../vsto/how-to-programmatically-create-custom-folder-items.md)  
  
  