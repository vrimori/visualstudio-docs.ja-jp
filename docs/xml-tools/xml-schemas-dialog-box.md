---
title: '[XML スキーマ] ダイアログ ボックス'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: reference
ms.assetid: 0271fa26-2205-49bd-96e0-ae1441571808
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5357f762d2a7027db92ad1916acb279abdf23157
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "34693641"
---
# <a name="xml-schemas-dialog-box"></a>XML スキーマ ダイアログ ボックス

**XML スキーマ**どの XML スキーマ定義言語 (XSD) スキーマに関連付ける XML ドキュメントを選択するダイアログ ボックスを使用します。 スキーマ キャッシュにあるスキーマを選択することも、キャッシュ内に置かれていないスキーマを指定することもできます。 選択したスキーマは、スキーマ セットの一部と見なされます。 そのスキーマ セットは、IntelliSense と XML ドキュメントの検証に使用されます。

アクセスすることができます、 **XML スキーマ** ダイアログ ボックスをクリックするか、**スキーマ**ボタンを選択してまたはドキュメントのプロパティ ウィンドウで**スキーマ**から**XML**メニュー。

## <a name="uielement-list"></a>UIElement の一覧
 **使用します。**

 XML スキーマの使用方法を選択します。

-   **自動**です。 このスキーマは現在のドキュメントで使用されていませんが、自動的な関連付けには使用できます。 XML ドキュメントでこのスキーマの `targetNamespace` に一致する名前空間を宣言すると、スキーマが自動的に関連付けられ、スキーマ セットに含まれます。

-   **このスキーマを使用して**です。 このスキーマは、現在のドキュメントで使用されています。 ユーザーがこの列をクリックしてこのスキーマが使用されることを明示的に要求したか、一致する `targetNamespace` に基づいてスキーマが自動的に関連付けられたかのいずれかです。

-   **選択したスキーマを使用しないでください**です。 スキーマに一致する `targetNamespace` がある場合でも、このスキーマは現在のドキュメントで使用されません。 この設定は、スキーマ キャッシュまたはソリューションに同じスキーマのバージョンが複数存在する場合の競合を解決する際に役立ちます。

**Target Namespace**

XML スキーマに関連付けられているターゲット名前空間が表示されます。

**ファイル名**

XML スキーマ ファイル名が表示されます。

**[追加]**

開く、 **XSD スキーマを開く**ダイアログで、スキーマ セットに追加するその他のスキーマを選択することができます。 設定スキーマにスキーマを追加すると、**使用**に列の値が設定されている**このスキーマを使用して**です。

**削除**

現在選択されているスキーマをスキーマ セットから削除します。 この操作では、メモリ内のスキーマ キャッシュからスキーマが削除されますが、ファイル システムからは削除されません。

## <a name="see-also"></a>関連項目

- [XML エディターのコンポーネント](../xml-tools/xml-editor-components.md)
- [方法: を使用する XML スキーマの選択](../xml-tools/how-to-select-the-xml-schemas-to-use.md)
- [スキーマ キャッシュ](../xml-tools/schema-cache.md)