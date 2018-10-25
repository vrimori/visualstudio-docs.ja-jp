---
title: XML ドキュメントのプロパティ、プロパティ ウィンドウ |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9dbb34d9-02ea-4201-b445-c98a0eb0d6db
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: c93defe6f5c56966195f1514b5aa76464f6f3013
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49236562"
---
# <a name="xml-document-properties-properties-window"></a>XML ドキュメント プロパティと [プロパティ] ウィンドウ
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
**プロパティ**ウィンドウは、XML エディターでアクティブなドキュメントに関する基本的な情報を提供します。 使用可能なプロパティは、現在アクティブになっている XML ドキュメントの種類によって異なります。  
  
> [!NOTE]
>  XML ドキュメントのプロパティは、すべてソリューション内に保存されます。 このため、ソリューションを次に開いたときにプロパティの値を再入力する必要はありません。  
  
 **エンコード**  
 ファイルの文字エンコードです。 このプロパティを変更すると、XML 宣言の encoding 属性も変更されます。逆に、encoding 属性を変更すれば、このプロパティも変更されます。 新しいエンコードは、ファイルを保存する際にファイルをエンコードするために使用されます。  
  
 **入力**  
 XSLT スタイル シートに関連付けられた入力ドキュメントです。 使用されて、 **ShowXSLT 出力**コマンド。 参照を使用してドキュメントを選択することができます (**.**) ボタンをクリックします。  
  
 このプロパティが表示されるのは、XSLT ファイルが現在エディター ウィンドウでアクティブになっている場合のみになります。  
  
 **出力**  
 XML ドキュメントを変換するときに生成されるファイルです。  
  
 ファイルが指定されていない場合は、ファイル拡張子を決定する `method` 要素の `xsl:output` 属性に基づいて既定のファイル名が生成されます。 既定のファイルは、現在のユーザーの一時ディレクトリに置かれます。  
  
 **スキーマ**  
 検証に使用するスキーマです。 ボタンが表示されます、 **XSD スキーマ** ダイアログ ボックスで、使用するスキーマを選択するために使用できます。  
  
 スキーマへのパスを入力することもできます。 複数のスキーマを指定する場合は、スキーマのパスをそれぞれ二重引用符で囲む必要があります。  
  
 **スタイル シート**  
 ドキュメントを変換するために使用した XSLT ファイルと、 **Show XSLT Output**コマンドを使用します。 このフィールドが空白の場合ときに、 **Show XSLT Output**コマンドを使用して、エディターで指定された値を使用して、`xml-stylesheet`ファイル名をユーザーに求めます処理命令、ドキュメントの。  
  
 別のスタイル シートがあることを指定するこのプロパティを使用できます、XSLT ファイルを編集するには、際に使用される、 **Show XSLT Output**または**XSLT のデバッグ**コマンドを選択します。 たとえば、親のスタイル シートにインクルードされるスタイル シートを編集しているときに、そのように指定することができます。  
  
## <a name="see-also"></a>関連項目  
 [XML エディター](../xml-tools/xml-editor.md)   
 [XML エディターのコンポーネント](../xml-tools/xml-editor-components.md)



