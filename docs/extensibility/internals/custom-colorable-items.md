---
title: カスタムの配色可能な項目 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- colorable items
- language services, custom colorable items
ms.assetid: b4d0ddee-c04b-48dc-ba82-f6068570cef0
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 690770c2091d3c0a983b91b9a25afc3d3eb4b348
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54974020"
---
# <a name="custom-colorable-items"></a>カスタムの配色可能な項目
言語サービスの一部としてカスタムの配色可能な項目を実装することでの色分け、キーワードやコメントなどの種類の一覧をオーバーライドできます。  
  
## <a name="user-settings-of-colorable-items"></a>装飾が可能な項目のユーザー設定  
 表示することができます、**フォントおよび色** ダイアログ ボックスを選択して**オプション** 上、**ツール** メニューを選択し、**フォントおよび色** **環境**します。 など、表示を選択するときに**テキスト エディター**または**コマンド ウィンドウ**、**表示項目**リスト ボックスが表示されるすべての装飾が可能な項目を表示します。 表示して、フォント、サイズ、前景の色、および各装飾が可能な項目の背景色を変更できます。 選択内容は、レジストリ内のキャッシュに格納されているし、装飾が可能な項目の名前でアクセスします。  
  
## <a name="presentation-of-colorable-items"></a>装飾が可能な項目の表示  
 IDE の配色可能な項目のユーザー オーバーライドをによって処理されるため、**フォントおよび色** ダイアログ ボックスでのみ各カスタム装飾が可能な項目を名前を指定する必要があります。 この名前に表示されます、**表示項目**一覧。 装飾が可能な項目は、アルファベット順に表示されます。 言語サービスのカスタムの配色可能な項目をグループ化することができますを開始する各名、言語の名前、たとえば**NewLanguage - コメント**と**NewLanguage - キーワード**します。  
  
> [!CAUTION]
>  既存の装飾が可能な項目名の競合を回避するために装飾が可能な項目名には、言語の名前を含める必要があります。 開発中に、装飾が可能な項目の 1 つの名前を変更する場合は、初めてアクセスされた装飾が可能な項目が作成されたキャッシュをリセットする必要があります。 実験的なキャッシュをリセットすることができます、 **CreateExpInstance**ツールで、通常は、ディレクトリで、Visual Studio SDK と共にインストールされます。  
>   
>  *C:\Program Files (x86)\Microsoft Visual Studio 14.0\VSSDK\VisualStudioIntegration\Tools\Bin*
>   
>  キャッシュをリセットするには入力**CreateExpInstance/Reset**します。 詳細については**CreateExpInstance**を参照してください[CreateExpInstance ユーティリティ](../../extensibility/internals/createexpinstance-utility.md)します。  
  
 装飾が可能な項目の一覧の最初の項目が参照されていることはありません。 最初の項目は、0 の装飾が可能な項目のインデックスに対応し、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]は常に既定のテキストの色とその項目の属性に提供します。 この参照されていない項目の処理の最も簡単な方法では、最初の項目として一覧内のプレース ホルダーの装飾が可能な項目を指定します。  
  
## <a name="implement-custom-colorable-items"></a>カスタムの配色可能な項目を実装します。  
  
1. 言語キーワード、演算子、および識別子の例でどのような色分け表示する必要がありますを定義します。  
  
2. これらの装飾が可能な項目の列挙体を作成します。  
  
3. パーサーまたは列挙の値を持つスキャナーから返されたトークンの種類を関連付けます。  
  
    たとえば、トークンの種類を表す値には、カスタムの配色可能な項目の列挙型で同じ値可能性があります。  
  
4. 実装で、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A>メソッドで、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>オブジェクト、スキャナー、パーサーから返されたトークンの種類に対応する、カスタムの配色可能な項目の列挙体から値を持つ属性の一覧を入力します。  
  
5. 実装するクラスと同じで、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>インターフェイスを実装、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems>インターフェイスとその 2 つのメソッドでは、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A>と<xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A>します。  
  
6. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> インターフェイスを実装します。  
  
7. 24 ビットまたは高の色の値をサポートする場合は、実装することも、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem>インターフェイス。  
  
8. 言語サービス オブジェクトを含むリストを作成、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem>オブジェクト、スキャナー、パーサーが識別できる各装飾が可能な項目に 1 つ。  
  
    リスト内の各項目は、カスタムの配色可能な項目の列挙体から対応する値を使用してアクセスできます。 リストに列挙値のインデックスとして使用します。 一覧の最初の項目にアクセスしない、既定のテキストに対応するため、スタイルを[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]自体は常に処理します。 この一覧の先頭にプレース ホルダーの装飾が可能な項目を挿入することにより補うことができます。  
  
9. 実装で、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A>メソッド、カスタムの配色可能な項目一覧に項目の数を返します。  
  
10. 実装で、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A>メソッドでは、一覧から要求された装飾が可能な項目を返します。  
  
    実装する方法の例については、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem>と<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem>インターフェイスを参照してください<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem>します。  
  
## <a name="see-also"></a>関連項目  
 [従来の言語サービスのモデル](../../extensibility/internals/model-of-a-legacy-language-service.md)   
 [構文のカスタム エディターで色分け表示](../../extensibility/syntax-coloring-in-custom-editors.md)   
 [構文の色分け、従来の言語サービス](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)   
 [実装の構文の色分け表示](../../extensibility/internals/implementing-syntax-coloring.md)   
 [方法: 組み込みの配色可能な項目を使用して、](../../extensibility/internals/how-to-use-built-in-colorable-items.md)