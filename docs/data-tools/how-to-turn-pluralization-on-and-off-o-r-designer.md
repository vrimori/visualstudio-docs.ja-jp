---
title: '方法: 複数形化のオンとオフ (O R デザイナー)'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 9b693bc3-303a-40a9-97ee-9cef5ca3ae81
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: a8c477ac276ce0ff9c292dc42ba2f5f7d1e53dd9
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-turn-pluralization-on-and-off-or-designer"></a>方法: 複数形化のオンとオフ (O/R デザイナー)
既定では、秒またはから開きますで終わる名前を持つデータベース オブジェクトをドラッグすると、**サーバー エクスプ ローラー**/**データベース エクスプ ローラー**上に、 [LINQ to SQL ツールの Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)、単数形に複数形から生成されたエンティティ クラスの名前が変更されます。 この処理は、インスタンス化されたエンティティ クラスが単一のデータ レコードにマップされるという事実をより正確に表すために行われます。 たとえば、Customers テーブルを [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]に追加すると、Customer という名前のエンティティ クラスが生成されます。このクラスには、単一の顧客のみが保持されるためです。

> [!NOTE]
>  複数形化は、英語バージョンの Visual Studio でのみ、既定でオンになります。

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-turn-pluralization-on-and-off"></a>複数形化をオンまたはオフにするには

1.  **[ツール]** メニューの **[オプション]** をクリックします。

2.  **オプション** ダイアログ ボックスで、展開**データベース ツール**です。

    > [!NOTE]
    >  選択**すべての設定を表示する**場合、**データベース ツール**ノードは表示されません。

3.  をクリックして**O/R デザイナー**です。

4.  設定**名前の複数形化**に**有効** = **False**を設定する、[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]クラス名が変わらないようにします。

5.  設定**名前の複数形化**に**有効** = **True**に追加されたオブジェクトのクラス名に複数形化規則を適用する、[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]です。

## <a name="see-also"></a>関連項目

- [Visual Studio の LINQ to SQL ツール](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [Visual Studio でのデータへのアクセス](../data-tools/accessing-data-in-visual-studio.md)