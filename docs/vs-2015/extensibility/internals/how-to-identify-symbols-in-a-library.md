---
title: '方法: ライブラリでシンボルの識別 |Microsoft Docs'
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
- Call Browser tool, identifying symbols in the library
- Call Browser tool
ms.assetid: 8fb0de61-71e7-42d1-8b41-2ad915474384
caps.latest.revision: 22
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2f10cc65d30f8d9b2d58fa02822494ae7e6a6940
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47547070"
---
# <a name="how-to-identify-symbols-in-a-library"></a>方法: ライブラリでシンボルの識別
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[方法: ライブラリで特定のシンボル](https://docs.microsoft.com/visualstudio/extensibility/internals/how-to-identify-symbols-in-a-library)します。  
  
シンボル参照ツールでは、シンボルの階層ビューを表示します。 シンボルは、名前空間、オブジェクト、クラス、クラスのメンバー、およびその他の言語要素を表します。  
  
 階層内の各シンボルをシンボル ライブラリによって渡されたナビゲーション情報で識別できます、[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]次のインターフェイスを介してオブジェクト マネージャー。  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfoNode>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumNavInfoNodes>。  
  
 階層内の記号の場所は、シンボルを区別します。 これにより、特定のシンボルに移動する、シンボル参照ツールができます。 シンボルに一意な完全修飾パスは、場所を決定します。 パス内の各要素は、ノードです。 パスは、最上位のノードから始まり、特定のシンボルで終わります。 たとえば、M1 メソッドは、C1 クラスのメンバー、C1 が N1 の名前空間にある場合は、M1 メソッドの完全なパスは N1 です。C1 します。M1 します。 このパスには、3 つのノードが含まれています: N1、C1、M1 します。  
  
 ナビゲーション情報により、[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]オブジェクト マネージャーを選択して保持する階層で、シンボルを選択します。 別に 1 つの参照ツールから移動することができます。 使用中に**オブジェクト ブラウザー**でシンボルを参照する、[!INCLUDE[vcprvc](../../includes/vcprvc-md.md)]プロジェクト、メソッドを右クリックし、開始できる、**呼び出しブラウザー**呼び出し先のメソッドを表示するツール。  
  
 2 つの形式では、シンボルの場所について説明します。 正規の形式は、記号の完全修飾パスに基づきます。 階層の一意の記号の位置を表します。 これは、シンボル参照ツールの依存しません。 正規の形式の情報を取得する、[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]オブジェクト マネージャー呼び出し<xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumCanonicalNodes%2A>メソッド。 プレゼンテーションのフォームでは、特定のシンボル参照ツール内でシンボルの場所について説明します。 Hierarchicy 内の他の記号の位置に対する相対パス、記号の位置です。 特定のシンボルは、1 つだけの既定のパスが、いくつかのプレゼンテーション パスにあります。 たとえば、C1 クラス C2 クラスから継承され、両方のクラスは、N1 の名前空間には、**オブジェクト ブラウザー**次の階層ツリーを表示します。  
  
```  
N1  
    C1  
        Bases and Interfaces  
            C2  
    C2  
        Bases and Interfaces  
. . . . . . . . . . .  
  
```  
  
 この例での C2 クラスの既定のパスには、N1 + C2 です。 C2 のプレゼンテーションのパスには、C1 と「ベースおよびインターフェイス」のノードが含まれています: N1 + C1 +「ベースおよびインターフェイス」+ C2 します。  
  
 プレゼンテーションのフォームはをオブジェクトの manager 呼び出しを取得する<xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumPresentationNodes%2A>メソッド。  
  
## <a name="identifying-a-symbol-in-the-hierarchy"></a>階層内のシンボルを識別します。  
  
#### <a name="to-obtain-canonical-and-presentation-forms-information"></a>正規の取得、およびプレゼンテーションのフォーム情報  
  
1.  <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumCanonicalNodes%2A> メソッドを実装します。  
  
     オブジェクト マネージャーは、シンボルの既定のパスに含まれるノードの一覧を取得するには、このメソッドを呼び出します。  
  
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
  
     オブジェクト マネージャーは、シンボルのプレゼンテーションのパスに含まれるノードの一覧を取得するには、このメソッドを呼び出します。  
  
## <a name="see-also"></a>関連項目  
 [シンボル参照ツールのサポート](../../extensibility/internals/supporting-symbol-browsing-tools.md)   
 [方法: オブジェクト マネージャーにライブラリの登録](../../extensibility/internals/how-to-register-a-library-with-the-object-manager.md)   
 [方法: ライブラリによって提供されるシンボルのリストをオブジェクト マネージャーに公開する](../../extensibility/internals/how-to-expose-lists-of-symbols-provided-by-the-library-to-the-object-manager.md)

