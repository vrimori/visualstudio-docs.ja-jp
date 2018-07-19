---
title: '方法: 複数形化のオンとオフにする (O/R デザイナー)'
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
ms.openlocfilehash: 0a2d2e44efc284c38cfc450833839776effb9936
ms.sourcegitcommit: e9d1018a01af62c3dc5aeb6b325faba7e20bd496
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/28/2018
ms.locfileid: "37089384"
---
# <a name="how-to-turn-pluralization-on-and-off-or-designer"></a>方法: 複数形化のオンとオフにする (O/R デザイナー)
既定で s または ies からで終わる名前を持つデータベース オブジェクトをドラッグすると、**サーバー エクスプ ローラー**または**データベース エクスプ ローラー**上に、 [Visual Studio での LINQ to SQL ツール](../data-tools/linq-to-sql-tools-in-visual-studio2.md)、生成されたエンティティ クラスの名前は、複数形から単数形に変更が。 この処理は、インスタンス化されたエンティティ クラスが単一のデータ レコードにマップされるという事実をより正確に表すために行われます。 などの追加、`Customers`テーブル、 **O/R デザイナー**という名前のエンティティ クラスに`Customer`クラスは、単一の顧客のみのデータを保持するためです。

> [!NOTE]
>  複数形化は、英語バージョンの Visual Studio でのみ、既定でオンになります。

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-turn-pluralization-on-and-off"></a>複数形化をオンまたはオフにするには

1.  **[ツール]** メニューの **[オプション]** をクリックします。

2.  **オプション** ダイアログ ボックスで、展開**データベース ツール**します。

    > [!NOTE]
    >  選択**すべての設定を表示する**場合、**データベース ツール**ノードは表示されません。

3.  クリックして**O/R デザイナー**します。

4.  設定**名の複数形化**に**有効** = **False**を設定する、 **O/R デザイナー**クラス名を変更しないように.

5.  設定**名の複数形化**に**有効** = **True**に追加されたオブジェクトのクラス名に複数形化規則を適用する、 **O/Rデザイナー**します。

## <a name="see-also"></a>関連項目

- [Visual Studio での LINQ to SQL ツールします。](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [Visual Studio でのデータへのアクセス](../data-tools/accessing-data-in-visual-studio.md)