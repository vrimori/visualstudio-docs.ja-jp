---
title: コマンド処理 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - command handling
ms.assetid: 78f67d92-77f7-45cb-ad75-6e3346379cc3
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4198cf6bbed2d8f6172872e4f98f1edb4749e7d7
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53926321"
---
# <a name="command-handling"></a>コマンド処理
エディターでは、新しいコマンドを定義できます。 コマンドは通常、メニューのツールバー、またはコンテキスト メニューに表示されます。  
  
 コマンドとメニューの定義の詳細については、次を参照してください。[コマンド、メニュー、およびツールバー](../extensibility/internals/commands-menus-and-toolbars.md)します。  
  
 言語サービスがインターセプトすることで、エディターで表示されるコンテキスト メニューを制御することができます、<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>列挙体。 または、マーカーあたりごとに、コンテキスト メニューを制御できます。 詳細については、次を参照してください。[言語サービス フィルターの重要なコマンド](../extensibility/internals/important-commands-for-language-service-filters.md)します。  
  
## <a name="add-commands-to-the-editor-context-menu"></a>エディター コンテキスト メニューにコマンドを追加します。  
 コンテキスト メニューにコマンドを追加するには、一連の特定のグループに属しているメニュー コマンドをまず定義する必要があります。 次の例がから取得した、 *.vsct*チュートリアルの一部として生成されたファイル[チュートリアル。カスタム エディターに機能を追加](../extensibility/walkthrough-adding-features-to-a-custom-editor.md):  
  
 \<メニューの guid"guidCustomEditorCmdSet"id ="IDMX_RTF"優先度の = ="0x0000"型「コンテキスト」= >  
  
 \<親 guid ="guidCustomEditorCmdSet"id =「0」/>  
  
 \<文字列 >  
  
 \<ButtonText > CustomEditor コンテキスト メニュー\</ButtonText >  
  
 \<CommandName > CustomEditorContextMenu\</CommandName >  
  
 \</文字列 >  
  
 \</メニュー >  
  
 \</メニュー >  
  
 上のテキストがテキストをコンテキスト メニュー コマンドを追加します**CustomEditor コンテキスト メニュー**します。 メニューの GUID は、このエディターで作成されたコマンド セットの一部です。 型は、「コンテキスト」です。  
  
 定義する必要はありませんが、定義済みのコマンドを使用することも、 *.vsct*ファイル。 たとえば、確認、 *EditorPane.cs* Visual Studio パッケージ テンプレートによって生成されたファイル。 表示されますが、定義済みのコマンドのセットなど<xref:Microsoft.VisualStudio.VSConstants.VSStd97CmdID>によって定義された<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>、コマンド ハンドラーでなどの処理、`onSelectAll`メソッド。  
  
## <a name="see-also"></a>関連項目  
 [コマンド、メニューのおよびツールバー](../extensibility/internals/commands-menus-and-toolbars.md)