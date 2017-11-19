---
title: "方法: 使用する XML スキーマの選択 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d6fda3ef-d465-4788-8514-2f2d528d658c
caps.latest.revision: "2"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 50077e430d6d9f273dd4cd3e247de3df043804c4
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-select-the-xml-schemas-to-use"></a>方法: 使用する XML スキーマを選択する
XML エディターはスキーマ キャッシュを提供します。このキャッシュは %InstallDir%\Xml\Schemas ディレクトリに配置されています。 スキーマ キャッシュには、IntelliSense と XML ドキュメントの検証に使用される既知の XML スキーマが格納されています。  
  
 **スキーマ**ドキュメント プロパティの使用を 1 つまたは複数 XML スキーマ定義言語 (XSD) スキーマを使用するを選択します。 このプロパティによって、スキーマ キャッシュにあるスキーマの選択、またはキャッシュ内に置かれていないスキーマの指定が可能になります。  
  
 指定したスキーマは、他のすべての XML ドキュメント プロパティと共に非表示のソリューション ユーザー オプション ファイル (.suo) に保存されます。 このため、ソリューションを次に開いたときにプロパティの値を再入力する必要はありません。  
  
> [!NOTE]
>  エディターは、インライン スキーマ、または `xsd:schemaLocation` 属性によって参照されているスキーマを使用して検証を行うことができます。 詳細については、次を参照してください。 [XML ドキュメントの検証](../xml-tools/xml-document-validation.md)です。  
  
### <a name="to-select-an-xml-schema-from-the-schema-cache"></a>スキーマ キャッシュにある XML スキーマを選択するには  
  
1.  XML エディターでファイルを開きます。  
  
2.  ドキュメントのプロパティ ウィンドウで、ボタンをクリックして、**スキーマ**フィールドです。  
  
     **XML スキーマ** ダイアログ ボックスが表示されます。 ダイアログ ボックスの一覧 (catalog.xml ファイルで参照されているスキーマを含む)、スキーマ キャッシュに .xsd 拡張子を持つすべてのスキーマとで参照されている Visual Studio で、現在のソリューション内にある任意のスキーマを開くことも、`xsd:schemaLocation`属性、またはで参照されています。**スキーマ**プロパティです。  
  
3.  次のいずれかを実行し、検証に使用するスキーマを選択します。  
  
    -   表示されているスキーマを選択、 **XML スキーマ**ダイアログ ボックスで、をクリックして、**使用**列、および選択**このスキーマを使用して**です。  
  
     または  
  
    -   表示されている複数のスキーマを選択して、 **XML スキーマ**ダイアログ、右クリックして選択**このスキーマを使用して**です。  
  
4.  **[OK]** をクリックします。  
  
     選択したスキーマの一覧にコピー、**スキーマ**プロパティを文書化します。  
  
### <a name="to-add-an-xml-schema-to-the-schema-cache"></a>XML スキーマをスキーマ キャッシュに追加するには  
  
1.  ドキュメントのプロパティ ウィンドウで、ボタンをクリックして、**スキーマ**フィールドです。  
  
2.  **[追加]**をクリックします。  
  
     開き、 **XSD スキーマを開く**ダイアログ。  
  
3.  スキーマ キャッシュに追加するスキーマを参照し、選択します。  
  
4.  をクリックして**開く**です。  
  
     スキーマに追加するスキーマのキャッシュし、は、**使用**に列の値が設定されている**このスキーマを使用して**です。  
  
### <a name="to-delete-an-xml-schema-from-the-schema-cache"></a>スキーマ キャッシュにある XML スキーマを削除するには  
  
1.  ドキュメントのプロパティ ウィンドウで、ボタンをクリックして、**スキーマ**フィールドです。  
  
2.  クリックして削除するスキーマを選択**削除**です。  
  
     スキーマは、メモリ内のスキーマ キャッシュから削除されますが、ファイル システムからは削除されません。  
  
    > [!NOTE]
    >  使用してスキーマへの参照があるかどうか、`schemaLocation`属性、または一致する`targetNamespace`し**削除**自動的な関連付けによりこの状況では機能しません。 ここではお勧めときにスキーマをマークする**選択されているスキーマを使用しないでください**で、**使用**列です。  
  
## <a name="see-also"></a>関連項目  
 [スキーマ キャッシュ](../xml-tools/schema-cache.md)   
 [XML スキーマ ダイアログ ボックス](../xml-tools/xml-schemas-dialog-box.md)   
 [XML エディター](../xml-tools/xml-editor.md)