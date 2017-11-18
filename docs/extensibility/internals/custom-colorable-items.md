---
title: "カスタムの装飾が可能な項目 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- colorable items
- language services, custom colorable items
ms.assetid: b4d0ddee-c04b-48dc-ba82-f6068570cef0
caps.latest.revision: "24"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b637e59b1e436c42b6b15f0dddaa1ed2ef6ff03c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="custom-colorable-items"></a>カスタムの装飾が可能な項目
言語サービスの一部としてカスタムの装飾が可能な項目を実装することによっての色分け、キーワードやコメントなどの種類の一覧をオーバーライドできます。  
  
## <a name="user-settings-of-colorable-items"></a>装飾が可能な項目のユーザー設定  
 表示することができます、**フォントおよび色** ダイアログ ボックスを選択して**オプション**上、**ツール** メニューを選択し、**フォントおよび色****環境**です。 など、表示を選択すると**テキスト エディター**または**コマンド ウィンドウ**、**項目を表示**リスト ボックスが表示されるすべての装飾が可能な項目を表示します。 表示して、フォント、サイズ、前景色、および各装飾が可能なアイテムの背景色を変更できます。 選択内容は、レジストリ内のキャッシュに格納されているし、装飾が可能な項目の名前でアクセスします。  
  
## <a name="presentation-of-colorable-items"></a>装飾が可能なアイテムの表示  
 IDE 内の装飾が可能な項目の上書きをユーザーが処理するため、**フォントおよび色**ダイアログ ボックスで、必要がある各カスタムの装飾が可能な項目を名前を指定するだけです。 この名前に表示される内容、**項目を表示** ボックスの一覧です。 装飾が可能な項目は、アルファベット順に表示されます。 言語サービスのカスタムの装飾が可能な項目をグループ化することができますを自分の言語名では、各名前たとえば**NewLanguage - コメント**と**NewLanguage - キーワード**です。  
  
> [!CAUTION]
>  既存の装飾が可能な項目の名前と衝突を避けるために装飾が可能な項目名には、言語の名前を含める必要があります。 開発中に装飾が可能な項目のいずれかの名前を変更する場合は、最初に装飾が可能な項目がアクセスされたときに作成されたキャッシュをリセットする必要があります。 通常は、ディレクトリで、Visual Studio SDK と共にインストールされる CreateExpInstance ツールで実験的なキャッシュをリセットすることができます。  
>   
>  **C:\Program Files (x86) \Microsoft Visual Studio 14.0\VSSDK\VisualStudioIntegration\Tools\Bin**  
>   
>  キャッシュをリセットするには、呼び出す`CreateExpInstance /Reset`です。 CreateExpInstance の詳細については、次を参照してください。 [CreateExpInstance ユーティリティ](../../extensibility/internals/createexpinstance-utility.md)です。  
  
 装飾が可能な項目の一覧の最初の項目が参照されていません。 最初の項目は、0 の装飾が可能な項目のインデックスに対応し、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]既定テキストの色とその項目の属性を常に提供します。 参照されていない、この項目を処理する場合の最も簡単な方法では、最初の項目として、リスト内のプレース ホルダーの装飾が可能な項目を指定します。  
  
## <a name="implementing-custom-colorable-items"></a>カスタムの装飾が可能な項目を実装します。  
  
1.  どのような言語キーワード、演算子、および識別子などの色で表示する必要がありますを定義します。  
  
2.  これらの装飾が可能な項目の列挙体を作成します。  
  
3.  パーサーまたは列挙の値を持つスキャナーから返されたトークンの種類を関連付けます。  
  
     たとえば、トークンの種類を表す値には、カスタムの装飾が可能なアイテムの列挙型に同じ値可能性があります。  
  
4.  実装で、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A>メソッドで、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>オブジェクト、パーサーやスキャナーから返されたトークンの種類に対応する、カスタムの装飾が可能な項目列挙から値を使用して、属性の一覧を入力します。  
  
5.  実装するクラスと同じで、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>インターフェイスでは、実装、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems>インターフェイスとその 2 つのメソッドでは、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A>と<xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A>です。  
  
6.  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> インターフェイスを実装します。  
  
7.  実装する場合は 24 ビット、または高の色の値をサポートするために、また、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem>インターフェイスです。  
  
8.  言語サービス オブジェクトを含むリストを作成、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem>オブジェクト、パーサーやスキャナーが識別できる装飾が可能な項目ごとに 1 つです。  
  
     リスト内の各項目は、カスタムの装飾が可能なアイテムの列挙体から対応する値を使用してアクセスできます。 リストに列挙値のインデックスとして使用します。 一覧の最初の項目にアクセスしない、既定のテキストに対応しているためにスタイルを[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]自体は常に処理します。 この一覧の先頭にプレース ホルダーの装飾が可能な項目を挿入することによって補正できます。  
  
9. 実装で、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A>メソッドをカスタムの装飾が可能なアイテムの一覧で項目の数を返します。  
  
10. 実装で、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A>メソッド、一覧から要求された装飾が可能な項目を返します。  
  
 実装する方法の例については、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem>と<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem>インターフェイスを参照してください<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem>です。  
  
## <a name="see-also"></a>関連項目  
 [従来の言語サービスのモデル](../../extensibility/internals/model-of-a-legacy-language-service.md)   
 [カスタム エディターの構文の色分け](../../extensibility/syntax-coloring-in-custom-editors.md)   
 [従来の言語サービスの構文の色分け](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)   
 [構文の色分けを実装します。](../../extensibility/internals/implementing-syntax-coloring.md)   
 [方法: ビルトインの配色可能な項目の使用](../../extensibility/internals/how-to-use-built-in-colorable-items.md)