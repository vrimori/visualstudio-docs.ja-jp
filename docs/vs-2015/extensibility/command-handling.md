---
title: コマンド処理 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - command handling
ms.assetid: 78f67d92-77f7-45cb-ad75-6e3346379cc3
caps.latest.revision: 21
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 32bfe8ec88d0e2ad5a2b765dcff01f543fe59c18
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47538584"
---
# <a name="command-handling"></a>コマンド処理
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[コマンド処理](https://docs.microsoft.com/visualstudio/extensibility/command-handling)します。  
  
エディターでは、新しいコマンドを定義できます。 コマンドは通常、メニューのツールバー、またはコンテキスト メニューに表示されます。  
  
 コマンドとメニューの定義の詳細については、次を参照してください。[コマンド、メニュー、およびツールバー](../extensibility/internals/commands-menus-and-toolbars.md)します。  
  
 言語サービスがインターセプトすることで、エディターで表示されるコンテキスト メニューを制御することができます、<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>列挙体。 または、マーカーあたりごとに、コンテキスト メニューを制御できます。 詳細については、次を参照してください。[言語サービス フィルターの重要なコマンド](../extensibility/internals/important-commands-for-language-service-filters.md)します。  
  
## <a name="adding-commands-to-the-editor-context-menu"></a>エディター コンテキスト メニューにコマンドを追加します。  
 コンテキスト メニューにコマンドを追加するには、一連の特定のグループに属しているメニュー コマンドをまず定義する必要があります。 次の例は、チュートリアルの一部として生成された .vsct ファイルから取得[チュートリアル: カスタム エディター機能の追加](../extensibility/walkthrough-adding-features-to-a-custom-editor.md):  
  
 \<メニューの guid"guidCustomEditorCmdSet"id ="IDMX_RTF"優先度の = ="0x0000"型「コンテキスト」= >  
  
 \<親 guid ="guidCustomEditorCmdSet"id =「0」/>  
  
 \<文字列 >  
  
 \<ButtonText > CustomEditor コンテキスト メニュー\</ButtonText >  
  
 \<CommandName > CustomEditorContextMenu\</CommandName >  
  
 \</文字列 >  
  
 \</メニュー >  
  
 \</メニュー >  
  
 上のテキストがテキストをコンテキスト メニュー コマンドを追加します**CustomEditor コンテキスト メニュー**します。 メニューの GUID は、このエディターで作成され、コマンド セットの型は、「コンテキスト」です。  
  
 .Vsct ファイルで定義する必要はありませんが、定義済みのコマンドを使用することもできます。 たとえば、Visual Studio パッケージ テンプレートによって生成された、EditorPane.cs ファイルを確認すると、見つかった場合一連の定義済みのコマンドなど<xref:Microsoft.VisualStudio.VSConstants.VSStd97CmdID>によって定義された<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>、onSelectAll メソッドなどのコマンド ハンドラーで処理されます。  
  
## <a name="see-also"></a>関連項目  
 [コマンド、メニュー、およびツール バー](../extensibility/internals/commands-menus-and-toolbars.md)

