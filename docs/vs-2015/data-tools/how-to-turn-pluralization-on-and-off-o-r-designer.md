---
title: '方法: 複数形化のオンとオフにする (O/R デザイナー) |Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9b693bc3-303a-40a9-97ee-9cef5ca3ae81
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 1f4491f25a861b8556ae5018e526349d6a17187a
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49279111"
---
# <a name="how-to-turn-pluralization-on-and-off-or-designer"></a>方法: 複数形化のオンとオフにする (O/R デザイナー)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
既定で s または ies からで終わる名前を持つデータベース オブジェクトをドラッグすると、**サーバー エクスプ ローラー**/**データベース エクスプ ローラー**上に、 [LINQ to SQL ツールでは、Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)、生成されたエンティティ クラスの名前は、複数形から単数形に変更されます。 この処理は、インスタンス化されたエンティティ クラスが単一のデータ レコードにマップされるという事実をより正確に表すために行われます。 たとえば、Customers テーブルを [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]に追加すると、Customer という名前のエンティティ クラスが生成されます。このクラスには、単一の顧客のみが保持されるためです。  
  
> [!NOTE]
>  複数形化は、英語バージョンの Visual Studio でのみ、既定でオンになります。  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
### <a name="to-turn-pluralization-on-and-off"></a>複数形化をオンまたはオフにするには  
  
1.  **[ツール]** メニューの **[オプション]** をクリックします。  
  
2.  **オプション** ダイアログ ボックスで、展開**データベース ツール**します。  
  
> [!NOTE]
>  選択**すべての設定を表示する**場合、**データベース ツール**ノードは表示されません。  
  
1.  クリックして**O/R デザイナー**します。  
  
2.  設定**名の複数形化**に**有効** = **False**を設定する、[!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]クラス名を変更しないようにします。  
  
3.  設定**名の複数形化**に**有効** = **True**に追加されたオブジェクトのクラス名に複数形化規則を適用する、[!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]します。  
  
## <a name="see-also"></a>関連項目  
 [LINQ to Visual Studio での SQL ツール](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)   
 [Visual Studio でのデータへのアクセス](../data-tools/accessing-data-in-visual-studio.md)

