---
title: '方法: 使用する XML スキーマの選択 |Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d6fda3ef-d465-4788-8514-2f2d528d658c
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 25e972b7c9850018aeda01401a8893805d3d18d6
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47533618"
---
# <a name="how-to-select-the-xml-schemas-to-use"></a>方法: 使用する XML スキーマを選択する
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[方法: 使用する XML スキーマを選択](https://docs.microsoft.com/visualstudio/xml-tools/how-to-select-the-xml-schemas-to-use)します。  
  
  
XML エディターはスキーマ キャッシュを提供します。このキャッシュは %InstallDir%\Xml\Schemas ディレクトリに配置されています。 スキーマ キャッシュには、IntelliSense と XML ドキュメントの検証に使用される既知の XML スキーマが格納されています。  
  
 **スキーマ**ドキュメント プロパティを使用して、1 つまたは複数 XML スキーマ定義言語 (XSD) スキーマを使用するを選択します。 このプロパティによって、スキーマ キャッシュにあるスキーマの選択、またはキャッシュ内に置かれていないスキーマの指定が可能になります。  
  
 指定したスキーマは、他のすべての XML ドキュメント プロパティと共に非表示のソリューション ユーザー オプション ファイル (.suo) に保存されます。 このため、ソリューションを次に開いたときにプロパティの値を再入力する必要はありません。  
  
> [!NOTE]
>  エディターは、インライン スキーマ、または `xsd:schemaLocation` 属性によって参照されているスキーマを使用して検証を行うことができます。 詳細については、次を参照してください。 [XML ドキュメントの検証](../xml-tools/xml-document-validation.md)です。  
  
### <a name="to-select-an-xml-schema-from-the-schema-cache"></a>スキーマ キャッシュにある XML スキーマを選択するには  
  
1.  XML エディターでファイルを開きます。  
  
2.  ドキュメントのプロパティ ウィンドウでのボタンをクリックします。、**スキーマ**フィールド。  
  
     **XML スキーマ** ダイアログ ボックスが表示されます。 ダイアログ ボックスの一覧 (catalog.xml ファイルで参照されるスキーマを含む)、スキーマ キャッシュに .xsd 拡張子を持つすべてのスキーマと、現在のソリューション内にある任意のスキーマで参照されている Visual Studio で開くことも、`xsd:schemaLocation`属性、またはで参照されています。**スキーマ**プロパティ。  
  
3.  次のいずれかを実行し、検証に使用するスキーマを選択します。  
  
    -   表示されているスキーマを選択、 **XML スキーマ**ダイアログ ボックスで、をクリックして、**使用**列、および選択し**このスキーマを使用して、** します。  
  
     - または -  
  
    -   一覧表示される複数のスキーマを選択、 **XML スキーマ**ダイアログ、右クリックして選択**このスキーマを使用して、** します。  
  
4.  **[OK]** をクリックします。  
  
     選択したスキーマの一覧は、元にコピーされる、**スキーマ**ドキュメントのプロパティ。  
  
### <a name="to-add-an-xml-schema-to-the-schema-cache"></a>XML スキーマをスキーマ キャッシュに追加するには  
  
1.  ドキュメントのプロパティ ウィンドウでのボタンをクリックします。、**スキーマ**フィールド。  
  
2.  **[追加]** をクリックします。  
  
     開き、 **XSD スキーマを開く**ダイアログ。  
  
3.  スキーマ キャッシュに追加するスキーマを参照し、選択します。  
  
4.  クリックして**オープン**します。  
  
     スキーマに追加するスキーマのキャッシュし、は、**使用**列の値に設定されて**このスキーマを使用して、** します。  
  
### <a name="to-delete-an-xml-schema-from-the-schema-cache"></a>スキーマ キャッシュにある XML スキーマを削除するには  
  
1.  ドキュメントのプロパティ ウィンドウでのボタンをクリックします。、**スキーマ**フィールド。  
  
2.  クリックして削除するスキーマを選択**削除**します。  
  
     スキーマは、メモリ内のスキーマ キャッシュから削除されますが、ファイル システムからは削除されません。  
  
    > [!NOTE]
    >  使用してスキーマへの参照があるかどうか、`schemaLocation`属性、または、一致する`targetNamespace`し**削除**自動的な関連付けによりこのような状況では機能しません。 ここでお勧めときにスキーマをマークする**選択されているスキーマを使用しないでください**で、**使用**列。  
  
## <a name="see-also"></a>関連項目  
 [スキーマ キャッシュ](../xml-tools/schema-cache.md)   
 [XML スキーマ ダイアログ ボックス](../xml-tools/xml-schemas-dialog-box.md)   
 [XML エディター](../xml-tools/xml-editor.md)



