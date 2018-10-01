---
title: '方法: XSLT でブレークポイントを使用する |Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bf7bbc2c-71dc-4cac-a6fc-add6b27d92ed
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 30ddb1fa8d56a55c5fc7a9811e4c836cabe4da0c
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47537425"
---
# <a name="how-to-use-breakpoints-with-xslt"></a>方法 : XSLT でブレークポイントを使用する
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

XSLT スタイル シート内または XML ソース ドキュメント内でブレークポイントを設定することができます。 タグにブレークポイントを設定した場合は、実行の開始時に、ソース行情報を含む次のステートメントにブレークポイントが移動します。  
  
 詳細については、次を参照してください。[デバッグの基礎: ブレークポイント](http://msdn.microsoft.com/en-us/752a02c2-0ac7-4c8b-aa1b-4b2b3b21152e)します。  
  
## <a name="set-a-breakpoint-in-a-style-sheet"></a>スタイル シート内にブレークポイントを設定する  
 XSLT スタイル シートでは、開始タグ、終了タグ、およびテキスト ノードにブレークポイントを設定できます。 スクリプト ブロック内のコードにブレークポイントを設定することもできます。  
  
#### <a name="to-set-a-breakpoint-in-a-style-sheet"></a>スタイル シート内にブレークポイントを設定するには  
  
1.  XML エディターでスタイル シートを開きます。  
  
2.  ブレークポイントの位置にカーソルを置き、右クリックし、 をポイント**ブレークポイント**、 をクリック**ブレークポイントの挿入**します。  
  
3.  参照ボタンをクリックします (**.**) で、**入力**ドキュメントのプロパティ ウィンドウのフィールド。  
  
4.  XML ソース ドキュメントを見つけてクリックして**オープン**します。  
  
     これで、XSLT 変換のために使用されるソース ドキュメント ファイルが設定されます。  
  
5.  をクリックして、 **XSL のデバッグ**XML エディターのツールバーのボタンをクリックします。  
  
## <a name="set-a-breakpoint-in-an-xml-source-document"></a>XML ソース ドキュメント内にブレークポイントを設定する  
 XML ソース ドキュメントでは、要素、属性、名前空間ノード、コメント、処理命令、およびテキスト ノードにブレークポイントを設定できます。 ドキュメント ノード、または、親要素から継承された名前空間ノードにブレークポイントを設定することはできません。  
  
#### <a name="to-set-a-breakpoint-in-an-xml-source-document"></a>XML ソース ドキュメント内にブレークポイントを設定するには  
  
1.  XML エディターで XML ドキュメントを開きます。  
  
2.  ブレークポイントの位置にカーソルを置き、右クリックし、 をポイント**ブレークポイント**、 をクリック**ブレークポイントの挿入**します。  
  
3.  参照ボタンをクリックします (**.**) で、 **Stylesheet**ドキュメントのプロパティ ウィンドウのフィールド。  
  
4.  XML ソース ドキュメントを見つけてクリックして**オープン**します。  
  
     これで、XSLT 変換のために使用されるソース ドキュメント ファイルが設定されます。  
  
5.  をクリックして、 **XSL のデバッグ**XML エディターのツールバーのボタンをクリックします。  
  
## <a name="see-also"></a>関連項目  
 [チュートリアル : XSLT スタイル シートのデバッグ](../xml-tools/walkthrough-debug-an-xslt-style-sheet.md)

