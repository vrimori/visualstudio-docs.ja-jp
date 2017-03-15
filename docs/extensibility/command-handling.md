---
title: "コマンド処理 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "エディター [Visual Studio SDK] - レガシ コマンド処理"
ms.assetid: 78f67d92-77f7-45cb-ad75-6e3346379cc3
caps.latest.revision: 20
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 20
---
# コマンド処理
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

エディターには、新しいコマンドを定義できます。 コマンドは通常、メニュー、ツール バーやコンテキスト メニューに表示されます。  
  
 コマンドおよびメニューを定義する方法の詳細については、次を参照してください。 [コマンド、メニュー、およびツールバー](../extensibility/internals/commands-menus-and-toolbars.md)します。  
  
 言語サービスがインターセプトすることで、エディターで表示されるコンテキスト メニューを制御することができます、 <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> 列挙します。 代わりに、マーカー単位ごとに、コンテキスト メニューを制御できます。 詳細については、次を参照してください。 [言語サービスのフィルターの重要なコマンド](../extensibility/internals/important-commands-for-language-service-filters.md)します。  
  
## <a name="adding-commands-to-the-editor-context-menu"></a>エディター コンテキスト メニューにコマンドを追加します。  
 コンテキスト メニューにコマンドを追加するには、最初に、特定のグループに属するメニュー コマンドのセットを定義する必要があります。 次の例は、チュートリアルの一部として生成された .vsct ファイルから取得 [チュートリアル: カスタム エディターに追加する機能](../extensibility/walkthrough-adding-features-to-a-custom-editor.md):  
  
 \< メニュー guid"guidCustomEditorCmdSet"id ="IDMX_RTF"優先度の = ="0x0000"型"context">  
  
 \< 親 guid ="guidCustomEditorCmdSet"id =「0」/>  
  
 \< 文字列>  
  
 \< ButtonText>CustomEditor コンテキスト メニュー \</アドイン>  
  
 \< CommandName>CustomEditorContextMenu \</CommandName>  
  
 \< 文字列/>  
  
 \</メニュー>  
  
 \</メニュー>  
  
 上のテキストがテキストでコンテキスト メニュー コマンドを追加 **CustomEditor コンテキスト メニュー**します。 メニューの GUID は、このエディターを使用して作成される一連のコマンドの種類は「コンテキスト」です。  
  
 .Vsct ファイルで定義する必要はありませんが、定義済みのコマンドを使用することもできます。 たとえば、Visual Studio パッケージ テンプレートによって生成された EditorPane.cs ファイルを調べると、見つかった場合、一連の定義済みのコマンドなど <xref:Microsoft.VisualStudio.VSConstants.VSStd97CmdID> によって定義された <xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>, 、onSelectAll メソッドなどのコマンド ハンドラーで処理されます。  
  
## <a name="see-also"></a>参照  
 [コマンド、メニューのおよびツールバー](../extensibility/internals/commands-menus-and-toolbars.md)