---
title: コマンド処理 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
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
ms.openlocfilehash: de4bf6ace6860cbd6155fe67a0de824e5626cfe3
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49257219"
---
# <a name="command-handling"></a>コマンド処理
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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

