---
title: XML スキーマ ダイアログ ボックス |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0271fa26-2205-49bd-96e0-ae1441571808
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e229919a625241f270090eb59be4aa8cd478c18c
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49251694"
---
# <a name="xml-schemas-dialog-box"></a>[XML スキーマ] ダイアログ ボックス
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
**XML スキーマ**どの XML スキーマ定義言語 (XSD) スキーマ、XML ドキュメントに関連付けるを選択するダイアログ ボックスを使用します。 スキーマ キャッシュにあるスキーマを選択することも、キャッシュ内に置かれていないスキーマを指定することもできます。 選択したスキーマは、スキーマ セットの一部と見なされます。 そのスキーマ セットは、IntelliSense と XML ドキュメントの検証に使用されます。  
  
 アクセスできる、 **XML スキーマ** ダイアログ ボックスをクリックするか、**スキーマ**ドキュメントのプロパティ ウィンドウで、または選択してボタン**スキーマ**から**XML**メニュー。  
  
## <a name="uielement-list"></a>UIElement の一覧  
 **使用**  
 XML スキーマの使用方法を選択します。  
  
-   **自動**します。 このスキーマは現在のドキュメントで使用されていませんが、自動的な関連付けには使用できます。 XML ドキュメントでこのスキーマの `targetNamespace` に一致する名前空間を宣言すると、スキーマが自動的に関連付けられ、スキーマ セットに含まれます。  
  
-   **このスキーマを使用して、** します。 このスキーマは、現在のドキュメントで使用されています。 ユーザーがこの列をクリックしてこのスキーマが使用されることを明示的に要求したか、一致する `targetNamespace` に基づいてスキーマが自動的に関連付けられたかのいずれかです。  
  
-   **選択したスキーマを使用しないでください**します。 スキーマに一致する `targetNamespace` がある場合でも、このスキーマは現在のドキュメントで使用されません。 この設定は、スキーマ キャッシュまたはソリューションに同じスキーマのバージョンが複数存在する場合の競合を解決する際に役立ちます。  
  
 **Target Namespace**  
 XML スキーマに関連付けられているターゲット名前空間が表示されます。  
  
 **ファイル名**  
 XML スキーマ ファイル名が表示されます。  
  
 **[追加]**  
 開く、 **XSD スキーマを開く**ダイアログ ボックスで、スキーマ セットに追加するその他のスキーマを選択することができます。 設定のスキーマにスキーマを追加すると、**使用**列の値に設定されて**このスキーマを使用して、** します。  
  
 **削除**  
 現在選択されているスキーマをスキーマ セットから削除します。 この操作では、メモリ内のスキーマ キャッシュからスキーマが削除されますが、ファイル システムからは削除されません。  
  
## <a name="see-also"></a>関連項目  
 [XML エディターのコンポーネント](../xml-tools/xml-editor-components.md)   
 [方法: 使用する XML スキーマを選択します。](../xml-tools/how-to-select-the-xml-schemas-to-use.md)   
 [スキーマ キャッシュ](../xml-tools/schema-cache.md)



