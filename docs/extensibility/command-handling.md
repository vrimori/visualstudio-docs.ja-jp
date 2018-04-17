---
title: コマンド処理 |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - command handling
ms.assetid: 78f67d92-77f7-45cb-ad75-6e3346379cc3
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 542277c5d8ab1b9b130f31bbb06215d8da7bc2ef
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="command-handling"></a>コマンド処理
エディターには、新しいコマンドを定義できます。 コマンドは通常、ツールバー、またはコンテキスト メニューのメニューに表示されます。  
  
 コマンドおよびメニューの定義の詳細については、次を参照してください。[コマンド、メニュー、およびツールバー](../extensibility/internals/commands-menus-and-toolbars.md)です。  
  
 言語サービスがインターセプトし、エディターで、表示されるコンテキスト メニューを制御することができます、<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>列挙します。 代わりに、マーカーあたりごとに、コンテキスト メニューを制御できます。 詳細については、次を参照してください。[言語サービスのフィルターの重要なコマンド](../extensibility/internals/important-commands-for-language-service-filters.md)です。  
  
## <a name="adding-commands-to-the-editor-context-menu"></a>エディター コンテキスト メニューにコマンドを追加します。  
 コンテキスト メニューにコマンドを追加するには、最初一連の特定のグループに属しているメニュー コマンドを定義する必要があります。 次の例は、このチュートリアルの一部として生成 .vsct ファイルから取得[チュートリアル: カスタム エディターに追加する機能](../extensibility/walkthrough-adding-features-to-a-custom-editor.md):  
  
 \<メニューの guid"guidCustomEditorCmdSet"id ="IDMX_RTF"優先度を = ="0x0000"種類"context">  
  
 \<親 guid ="guidCustomEditorCmdSet"id =「0」/>  
  
 \<文字列 >  
  
 \<ButtonText > CustomEditor コンテキスト メニュー\</ButtonText >  
  
 \<CommandName > CustomEditorContextMenu\</CommandName >  
  
 \</文字列 >  
  
 \</メニュー >  
  
 \</メニュー >  
  
 上記のテキストを追加、コンテキスト メニューのコマンドをテキスト**CustomEditor コンテキスト メニュー**です。 メニュー GUID は、このエディターでは、コマンド セットの作成され、型が「コンテキスト」ことです。  
  
 .Vsct ファイルで定義する必要はありません定義済みのコマンドを使用することもできます。 たとえば、Visual Studio パッケージ テンプレートによって生成された EditorPane.cs ファイルを確認する場合と考えることが、定義済みのコマンドのセットなど<xref:Microsoft.VisualStudio.VSConstants.VSStd97CmdID>によって定義された<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>、onSelectAll メソッドなどのコマンド ハンドラーで処理されます。  
  
## <a name="see-also"></a>関連項目  
 [コマンド、メニュー、およびツール バー](../extensibility/internals/commands-menus-and-toolbars.md)