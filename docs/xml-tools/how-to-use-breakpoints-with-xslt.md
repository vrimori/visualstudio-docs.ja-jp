---
title: "方法: XSLT でブレークポイントを使用して |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bf7bbc2c-71dc-4cac-a6fc-add6b27d92ed
caps.latest.revision: "2"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 8c077cab7bf02023d0bfb1714940f98020600477
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-use-breakpoints-with-xslt"></a>方法 : XSLT でブレークポイントを使用する
XSLT スタイル シート内または XML ソース ドキュメント内でブレークポイントを設定することができます。 タグにブレークポイントを設定した場合は、実行の開始時に、ソース行情報を含む次のステートメントにブレークポイントが移動します。  
  
 詳細については、次を参照してください。[デバッグの基礎: ブレークポイント](http://msdn.microsoft.com/en-us/752a02c2-0ac7-4c8b-aa1b-4b2b3b21152e)です。  
  
## <a name="set-a-breakpoint-in-a-style-sheet"></a>スタイル シート内にブレークポイントを設定する  
 XSLT スタイル シートでは、開始タグ、終了タグ、およびテキスト ノードにブレークポイントを設定できます。 スクリプト ブロック内のコードにブレークポイントを設定することもできます。  
  
#### <a name="to-set-a-breakpoint-in-a-style-sheet"></a>スタイル シート内にブレークポイントを設定するには  
  
1.  XML エディターでスタイル シートを開きます。  
  
2.  ブレークポイントの場所にカーソルを置き、右クリックし、順にポイント**ブレークポイント**、 をクリック**ブレークポイントの挿入**です。  
  
3.  参照ボタンをクリックして (**.**) で、**入力**ドキュメントのプロパティ ウィンドウのフィールドです。  
  
4.  XML ソース ドキュメントを見つけてクリックして**開く**です。  
  
     これで、XSLT 変換のために使用されるソース ドキュメント ファイルが設定されます。  
  
5.  クリックして、 **XSL のデバッグ**XML エディター ツールバーのボタンをクリックします。  
  
## <a name="set-a-breakpoint-in-an-xml-source-document"></a>XML ソース ドキュメント内にブレークポイントを設定する  
 XML ソース ドキュメントでは、要素、属性、名前空間ノード、コメント、処理命令、およびテキスト ノードにブレークポイントを設定できます。 ドキュメント ノード、または、親要素から継承された名前空間ノードにブレークポイントを設定することはできません。  
  
#### <a name="to-set-a-breakpoint-in-an-xml-source-document"></a>XML ソース ドキュメント内にブレークポイントを設定するには  
  
1.  XML エディターで XML ドキュメントを開きます。  
  
2.  ブレークポイントの場所にカーソルを置き、右クリックし、順にポイント**ブレークポイント**、 をクリック**ブレークポイントの挿入**です。  
  
3.  参照ボタンをクリックして (**.**) で、 **Stylesheet**ドキュメントのプロパティ ウィンドウのフィールドです。  
  
4.  XML ソース ドキュメントを見つけてクリックして**開く**です。  
  
     これで、XSLT 変換のために使用されるソース ドキュメント ファイルが設定されます。  
  
5.  クリックして、 **XSL のデバッグ**XML エディター ツールバーのボタンをクリックします。  
  
## <a name="see-also"></a>関連項目  
 [チュートリアル : XSLT スタイル シートのデバッグ](../xml-tools/walkthrough-debug-an-xslt-style-sheet.md)