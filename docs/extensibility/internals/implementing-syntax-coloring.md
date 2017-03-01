---
title: "構文の色分けを実装する |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- syntax coloring, implementing
- editors [Visual Studio SDK], colorizing text
- text, colorizing in editors
ms.assetid: 96e762ca-efd0-41e7-8958-fda4897c8c7a
caps.latest.revision: 20
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 67535bcc2c907978c24d764c617f8311dc51a444
ms.lasthandoff: 02/22/2017

---
# <a name="implementing-syntax-coloring"></a>構文の色分けを実装します。
言語サービスは、構文の色表示機能を提供、パーサーは、行のテキストを装飾が可能な項目の配列に変換し、これらの装飾が可能な項目に対応するトークンの種類を返します。 パーサーは、装飾が可能な項目の一覧に属しているトークンの種類を返す必要があります。 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]colorizer オブジェクトによって適切なトークンの種類に割り当てられた属性に基づいて、コード ウィンドウ内の各装飾が可能な項目を表示します。  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]パーサー インターフェイスが指定されていないと、パーサーの実装が決定します。 ただし、既定のパーサー実装は、Visual Studio 言語パッケージ プロジェクトで提供されます。 マネージ コード用のマネージ パッケージ フレームワーク (MPF) はのテキストを色分けする完全なサポートを提供します。  
  
 従来の言語サービスは、VSPackage の一部として実装されますが、言語サービスの機能を実装する新しい方法は、MEF の拡張機能を使用します。 構文の色分けを実装する新しい方法の詳細については、次を参照してください。[チュートリアル: テキストの強調表示](../../extensibility/walkthrough-highlighting-text.md)します。  
  
> [!NOTE]
>  エディターを使用して、新しい API できるだけ早く始めることをお勧めします。 言語サービスのパフォーマンスを向上させる、エディターの新機能を活用できます。  
  
## <a name="steps-followed-by-an-editor-to-colorize-text"></a>手順の後に、エディターのテキストを色分けして表示するには  
  
1.  エディターを呼び出して、colorizer の取得、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A>メソッドを<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>オブジェクト</xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo></xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A>。  
  
2.  エディターの呼び出し、 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.GetStateMaintenanceFlag%2A>、colorizer に、colorizer の外部に保持するには、各ラインの状態が必要かどうかを決定する方法</xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.GetStateMaintenanceFlag%2A>。  
  
3.  エディターを呼び出す、colorizer では、状態を colorizer の外部に保持する必要がある場合、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.GetStartState%2A>最初の行の状態を取得します</xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.GetStartState%2A>。  
  
4.  エディターを呼び出し、バッファーの各行に対して、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A>メソッドで、次の手順を実行します:</xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A>  
  
    1.  行のテキストは、テキストをトークンに変換するスキャナーに渡されます。 各トークンは、トークンのテキストとトークンの種類を指定します。  
  
    2.  トークン型は、装飾が可能な項目の一覧へのインデックスに変換されます。  
  
    3.  トークンの情報は、配列、配列の各要素は、行の文字に対応するようを埋めるために使用されます。 配列に格納された値は、装飾が可能な項目の一覧にインデックスです。  
  
    4.  行ごとに、行の末尾で、状態が返されます。  
  
5.  Colorizer では、状態を維持する必要がある場合、エディターは、その行の状態をキャッシュします。  
  
6.  エディターから返される情報を使用してテキストの行を表示する、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A>メソッド</xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A>。 この場合、次の手順が必要です。  
  
    1.  行内の各文字の装飾が可能な項目のインデックスを取得します。  
  
    2.  既定の装飾が可能な項目を使用する場合、エディターの装飾が可能な項目 一覧にアクセスします。  
  
    3.  それ以外の場合、サービスを呼び出し、言語の<xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A>装飾が可能な項目を取得します</xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A>。  
  
    4.  装飾が可能な項目の情報を使用して、ディスプレイにテキストを表示します。  
  
## <a name="managed-package-framework-colorizer"></a>マネージ パッケージ フレームワーク Colorizer  
 マネージ パッケージ フレームワーク (MPF) では、colorizer を実装するために必要なすべてのクラスを提供します。 言語サービス クラスを継承する必要があります、<xref:Microsoft.VisualStudio.Package.LanguageService>クラスし、必要なメソッドを実装します</xref:Microsoft.VisualStudio.Package.LanguageService>。 スキャナーとパーサーを実装することで指定する必要があります、<xref:Microsoft.VisualStudio.Package.IScanner>インターフェイス、およびからそのインターフェイスのインスタンスを返す、<xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A>メソッド (に実装する必要があるメソッドのいずれか、<xref:Microsoft.VisualStudio.Package.LanguageService>クラス).</xref:Microsoft.VisualStudio.Package.LanguageService> </xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> </xref:Microsoft.VisualStudio.Package.IScanner> 詳細については、次を参照してください。[レガシ言語サービスでの構文の色分け](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)します。  
  
## <a name="see-also"></a>関連項目  
 [方法: ビルトインの装飾が可能な項目を使用して](../../extensibility/internals/how-to-use-built-in-colorable-items.md)   
 [カスタムの装飾が可能な項目](../../extensibility/internals/custom-colorable-items.md)   
 [従来の言語サービスの開発](../../extensibility/internals/developing-a-legacy-language-service.md)   
 [従来の言語サービスでの構文の色分け](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)
