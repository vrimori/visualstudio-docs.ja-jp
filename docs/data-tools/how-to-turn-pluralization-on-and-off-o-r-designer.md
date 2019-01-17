---
title: '方法: 複数形化をオンおよびオフにする (O-R デザイナー)'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 9b693bc3-303a-40a9-97ee-9cef5ca3ae81
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: 99dc1c6fefae880d10c1dedd080f9abbceba4d1c
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53961765"
---
# <a name="how-to-turn-pluralization-on-and-off-or-designer"></a>方法: 複数形化をオンおよびオフにする (O/R デザイナー)
既定で s または ies からで終わる名前を持つデータベース オブジェクトをドラッグすると、**サーバー エクスプ ローラー**または**データベース エクスプ ローラー**上に、 [Visual Studio での LINQ to SQL ツール](../data-tools/linq-to-sql-tools-in-visual-studio2.md)、生成されたエンティティ クラスの名前は、複数形から単数形に変更が。 この処理は、インスタンス化されたエンティティ クラスが単一のデータ レコードにマップされるという事実をより正確に表すために行われます。 などの追加、`Customers`テーブル、 **O/R デザイナー**という名前のエンティティ クラスに`Customer`クラスは、単一の顧客のみのデータを保持するためです。

> [!NOTE]
>  複数形化は、英語バージョンの Visual Studio でのみ、既定でオンになります。

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-turn-pluralization-on-and-off"></a>複数形化をオンまたはオフにするには

1.  **[ツール]** メニューの **[オプション]** をクリックします。

2.  **[オプション]** ダイアログ ボックスの **[データベース ツール]** を展開します。

    > [!NOTE]
    >  **[データベース ツール]** ノードが表示されない場合は、**[すべての設定を表示]** を選択します。

3.  **[O/R デザイナー]** をクリックします。

4.  設定**名の複数形化**に**有効** = **False**を設定する、 **O/R デザイナー**クラス名を変更しないように.

5.  設定**名の複数形化**に**有効** = **True**に追加されたオブジェクトのクラス名に複数形化規則を適用する、 **O/Rデザイナー**します。

## <a name="see-also"></a>関連項目

- [Visual Studio の LINQ to SQL ツール](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [Visual Studio でのデータへのアクセス](../data-tools/accessing-data-in-visual-studio.md)