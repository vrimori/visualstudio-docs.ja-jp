---
title: "カスタムの装飾が可能な項目 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "装飾が可能な項目"
  - "言語サービス、カスタムの装飾が可能な項目"
ms.assetid: b4d0ddee-c04b-48dc-ba82-f6068570cef0
caps.latest.revision: 24
caps.handback.revision: 24
ms.author: "gregvanl"
manager: "ghogen"
---
# カスタムの装飾が可能な項目
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

言語サービスの一部としてカスタムの装飾が可能な項目を実装することでの色分け、キーワードやコメントなどの種類の一覧をオーバーライドできます。  
  
## 装飾が可能な項目のユーザー設定  
 表示することができます、 **フォントおよび色** \] ダイアログ ボックスを選択して **オプション** 上、 **ツール** \] メニューを選択し、 **フォントおよび色** \[ **環境**します。 など、表示を選択すると **テキスト エディター** または **コマンド ウィンドウ**, 、 **項目を表示** リスト ボックスが表示されるすべての装飾が可能な項目を表示します。 表示して、フォント、サイズ、前景色、および各装飾が可能な項目の背景色を変更できます。 選択内容は、レジストリ内のキャッシュに格納され、装飾が可能な項目の名前でアクセスします。  
  
## 装飾が可能な項目の表示  
 IDE 内の装飾が可能な項目のユーザー オーバーライドをによって処理されるため、 **フォントおよび色** ダイアログ ボックスで、する必要がある各カスタムの装飾が可能な項目を名前を指定するしかします。 この名前に表示される内容、 **項目を表示** \] ボックスの一覧です。 装飾が可能な項目は、アルファベット順に表示されます。 言語サービスのカスタムの装飾が可能な項目をグループ化することができます、言語の名前では、各名前たとえば **NewLanguage \- コメント** と **NewLanguage \- キーワード**します。  
  
> [!CAUTION]
>  既存の装飾が可能な項目の名前の衝突を避けるために装飾が可能な項目名、言語の名前を含める必要があります。 開発時に、装飾が可能な項目のいずれかの名前を変更する場合、装飾が可能な項目にアクセスされた最初のときに作成されたキャッシュをリセットする必要があります。 ディレクトリの通常の Visual Studio SDK と共にインストールされる CreateExpInstance ツールを使用して実験的なキャッシュをリセットします。  
>   
>  **C:\\Program ファイル \(x86\) \\Microsoft Visual Studio 14.0\\VSSDK\\VisualStudioIntegration\\Tools\\Bin**  
>   
>  キャッシュをリセットするには、呼び出す `CreateExpInstance /Reset`します。 CreateExpInstance の詳細については、次を参照してください。 [CreateExpInstance ユーティリティ](../../extensibility/internals/createexpinstance-utility.md)します。  
  
 装飾が可能な項目の一覧の最初の項目が参照されていることはありません。 最初の項目が 0 の装飾が可能な項目のインデックスに対応し、 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 常に既定のテキストの色とそのアイテムの属性を指定します。 参照されていない項目に対処する最も簡単な方法は、最初のアイテムとして一覧に、プレース ホルダーの装飾が可能な項目を提供することです。  
  
## カスタムの装飾が可能な項目を実装します。  
  
1.  キーワード、演算子、および識別子などの言語でどのような色分け表示する必要がありますを定義します。  
  
2.  これらの装飾が可能な項目の列挙体を作成します。  
  
3.  パーサーまたは列挙の値を持つスキャナーから返されたトークンの種類を関連付けます。  
  
     たとえば、トークンの型を表す値は、カスタムの装飾が可能な項目の列挙型に同じ値になります。  
  
4.  実装で、 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> メソッドで、 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> オブジェクト、パーサーまたはスキャナーから返されたトークンの種類に対応する、カスタムの装飾が可能な項目の列挙の値の属性リストを生成します。  
  
5.  実装するクラスと同じで、 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> インターフェイスを実装する、 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> インターフェイスとその 2 つのメソッド <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A> と <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A>です。  
  
6.  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> インターフェイスを実装します。  
  
7.  実装する場合は 24 ビットまたは高の色の値をサポートするために、また、 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> インターフェイスです。  
  
8.  言語サービスのオブジェクトの作成を含むリスト、 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> オブジェクト、パーサーやスキャナーが識別できる装飾が可能な項目ごとに 1 つです。  
  
     リスト内の各項目は、カスタムの装飾が可能な項目の列挙体から対応する値を使用してアクセスできます。 リストに列挙値のインデックスとして使用します。 一覧の最初の項目にアクセスしない、既定のテキストに対応するためのスタイルを [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 自体は常に処理します。 この一覧の先頭に、プレース ホルダーの装飾が可能な項目を挿入することによって補正できます。  
  
9. 実装で、 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A> メソッド、カスタムの装飾が可能な項目リストの項目の数を返します。  
  
10. 実装で、 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> メソッド、ユーザーの一覧から要求された装飾が可能な項目を返します。  
  
 実装する方法の例については、 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> と <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> インターフェイスを参照してください <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem>します。  
  
## 参照  
 [従来の言語サービスのモデル](../../extensibility/internals/model-of-a-legacy-language-service.md)   
 [構文のカスタム エディターの色指定](../../extensibility/syntax-coloring-in-custom-editors.md)   
 [構文の色分けで従来の言語サービス](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)   
 [構文の色分けを実装します。](../../extensibility/internals/implementing-syntax-coloring.md)   
 [方法: ビルトインの装飾が可能な項目を使用して](../../extensibility/internals/how-to-use-built-in-colorable-items.md)