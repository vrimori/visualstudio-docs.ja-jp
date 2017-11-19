---
title: "方法: ライブラリ内のシンボルを識別 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Call Browser tool, identifying symbols in the library
- Call Browser tool
ms.assetid: 8fb0de61-71e7-42d1-8b41-2ad915474384
caps.latest.revision: "21"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6e7f810ff5ad1654081cd061edbc4360eb988402
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-identify-symbols-in-a-library"></a>方法: ライブラリ内のシンボルの特定
シンボル参照のツールには、シンボルの階層ビューが表示されます。 シンボルは、名前空間、オブジェクト、クラス、クラス メンバー、およびその他の言語要素を表します。  
  
 階層内の各シンボルはシンボル ライブラリによって渡されたナビゲーション情報で識別できます、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]次のインターフェイスを介してオブジェクト マネージャー。  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfoNode>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumNavInfoNodes>。  
  
 階層内の記号の場所は、シンボルを区別します。 これにより、特定の記号に移動するためのツールのシンボル参照できます。 シンボルに一意な完全修飾パスでは、場所を決定します。 パス内の各要素は、ノードです。 パスは、最上位ノードから始まり、特定の記号で終わります。 たとえば、M1 メソッドは、C1 クラスのメンバーと、C1 が N1 の名前空間には、M1 メソッドの完全なパスは N1 です。C1 します。M1 です。 このパスには、3 つのノードが含まれています: N1、C1、および M1 です。  
  
 ナビゲーション情報により、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]を探して選択し、保持オブジェクト マネージャーは、階層で、シンボルを選択します。 これにより、1 つのブラウザー ツールから移動することができます。 使用しているときに**オブジェクト ブラウザー**内のシンボルを参照する、[!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]プロジェクト、メソッドを右クリックして、開始、**呼び出しブラウザー**呼び出し先のメソッドを表示するツールです。  
  
 2 つの形式では、シンボルの場所について説明します。 正規の形式は、記号の完全修飾パスに基づいています。 階層内のシンボルの一意の位置を表します。 これは、シンボル参照ツールの依存しません。 正規の形式情報を取得する、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]オブジェクト マネージャー呼び出し<xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumCanonicalNodes%2A>メソッドです。 プレゼンテーション フォームでは、特定のシンボル参照ツール内でシンボルの場所について説明します。 記号の位置、hierarchicy 内の他の記号の位置に対する相対パスです。 特定のシンボルは、正規のパスを 1 つだけですが、プレゼンテーションのいくつかのパスがあります。 たとえば、C1 クラス C2 クラスから継承され、両クラスは、N1 の名前空間には、**オブジェクト ブラウザー**次の階層ツリーが表示されます。  
  
```  
N1  
    C1  
        Bases and Interfaces  
            C2  
    C2  
        Bases and Interfaces  
. . . . . . . . . . .  
  
```  
  
 この例では、C2 クラスの既定のパスとは、N1 + C2 です。 C2 のプレゼンテーションのパスには、C1 および「基本およびインターフェイス」ノードが含まれています: N1 + C1 +「基本およびインターフェイス」+ C2 です。  
  
 プレゼンテーション形式については、オブジェクト マネージャーの呼び出しを取得する<xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumPresentationNodes%2A>メソッドです。  
  
## <a name="identifying-a-symbol-in-the-hierarchy"></a>階層内のシンボルを識別します。  
  
#### <a name="to-obtain-canonical-and-presentation-forms-information"></a>正規に取得するプレゼンテーション フォーム情報および  
  
1.  <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumCanonicalNodes%2A> メソッドを実装します。  
  
     オブジェクト マネージャーでは、シンボルの既定のパスに含まれているノードの一覧を取得するには、このメソッドを呼び出します。  
  
    ```vb  
    Public Function EnumCanonicalNodes(ByRef ppEnum As Microsoft.VisualStudio.Shell.Interop.IVsEnumNavInfoNodes) As Integer  
        Dim EnumNavInfoNodes As CallBrowserEnumNavInfoNodes = _New CallBrowserEnumNavInfoNodes(m_strMethod)  
        ppEnum = CType(EnumNavInfoNodes, IVsEnumNavInfoNodes)  
        Return 0  
    End Function  
    ```  
  
    ```csharp  
    public int EnumCanonicalNodes(out Microsoft.VisualStudio.Shell.Interop.IVsEnumNavInfoNodes ppEnum)  
    {  
        CallBrowserEnumNavInfoNodes EnumNavInfoNodes =  
            new CallBrowserEnumNavInfoNodes(m_strMethod);  
        ppEnum = (IVsEnumNavInfoNodes)(EnumNavInfoNodes);  
        return 0;  
    }  
  
    ```  
  
2.  <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumPresentationNodes%2A> メソッドを実装します。  
  
     オブジェクト マネージャーでは、シンボルのプレゼンテーション パスに含まれるノードの一覧を取得するには、このメソッドを呼び出します。  
  
## <a name="see-also"></a>関連項目  
 [シンボル参照のツールのサポート](../../extensibility/internals/supporting-symbol-browsing-tools.md)   
 [方法: オブジェクト マネージャーにライブラリを登録](../../extensibility/internals/how-to-register-a-library-with-the-object-manager.md)   
 [方法: ライブラリによって提供されるシンボルのリストをオブジェクト マネージャーに公開する](../../extensibility/internals/how-to-expose-lists-of-symbols-provided-by-the-library-to-the-object-manager.md)