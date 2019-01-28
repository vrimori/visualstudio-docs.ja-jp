---
title: '方法: プログラムによって特定のフォルダー内を検索します。'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Outlook folders [Office development in Visual Studio], searching
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: d9a08451b186cdc3ca1526441e906cf3c9e5d4c9
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2019
ms.locfileid: "54866845"
---
# <a name="how-to-programmatically-search-within-a-specific-folder"></a>方法: プログラムによって特定のフォルダー内を検索します。
  このコード例では、`Find`と`FindNext`内にある電子メール メッセージの件名フィールド内のテキストを検索する方法、**受信トレイ**します。 このメソッドでは、文字列のフィルターを使用して、t の開始文字確認、`Subject`テキスト。  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="example"></a>例  
 [!code-csharp[Trin_OL_SearchFolder#1](../vsto/codesnippet/CSharp/Trin_OL_SearchFolder/thisaddin.cs#1)]  
  
## <a name="see-also"></a>関連項目  
 [フォルダーを操作します。](../vsto/working-with-folders.md)   
 [Outlook オブジェクト モデルの概要](../vsto/outlook-object-model-overview.md)   
 [方法: 名前でフォルダーをプログラムで取得します。](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)  
