---
title: '方法: プログラムによって Outlook のフォルダー、web ページに関連付ける'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- folders [Office development in Visual Studio], Web pages and
- Outlook [Office development in Visual Studio], Web pages attached to folders
- Web pages [Office development in Visual Studio], Outlook folders
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: c60ac58c59adaacd66a7c56b4c394d596cfd6b24
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2019
ms.locfileid: "54871274"
---
# <a name="how-to-programmatically-associate-a-web-page-with-an-outlook-folder"></a>方法: プログラムによって Outlook のフォルダー、web ページに関連付ける
  この例は、という名前のフォルダーの`HtmlView`Microsoft Office Outlook でします。 フォルダーが存在しない場合、コードはフォルダーを作成し、Web ページを割り当てます。 フォルダーが存在する場合、コードはフォルダーの内容を表示します。  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="example"></a>例  
 [!code-csharp[Trin_OL_HTMLFolder#1](../vsto/codesnippet/CSharp/Trin_OL_HTMLFolder/thisaddin.cs#1)]  
  
## <a name="see-also"></a>関連項目  
 [フォルダーを操作します。](../vsto/working-with-folders.md)   
 [方法: 名前でフォルダーをプログラムで取得します。](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)   
 [方法: プログラムによってカスタム フォルダーのアイテムを作成します。](../vsto/how-to-programmatically-create-custom-folder-items.md)  
