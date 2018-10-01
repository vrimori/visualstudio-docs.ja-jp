---
title: マネージ コードの HRESULT 情報 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- VSPackages, HRESULT information
- HRESULT, managed VSPackages
ms.assetid: 0795ee94-17a8-4327-bf57-27cd5e312a4c
caps.latest.revision: 29
manager: douge
ms.openlocfilehash: c87fc618f1c80b60bbd2f95537dc70a83eb2bdc7
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47533847"
---
# <a name="hresult-information-in-managed-code"></a>マネージ コードの HRESULT 情報
マネージド コードと COM の相互作用によって、HRESULT 戻り値が検出されたときに問題が発生する可能性があります。  
  
 COM インターフェイスでは、HRESULT 戻り値が次の役割を果たします。  
  
-   エラー情報を提供 (たとえば、 <xref:Microsoft.VisualStudio.VSConstants.E_INVALIDARG>)。  
  
-   通常のプログラムの動作に関するステータス情報を提供します。  
  
 COM がマネージド コードへの呼び出しを行うと、HRESULT によって次の問題が発生する可能性があります。  
  
-   ゼロ未満の HRESULT 値 (エラー コード) を返す COM 関数によって、例外が生成されます。  
  
-   たとえば、2 つまたは複数の異なる成功コードを定期的に返す COM メソッド<xref:Microsoft.VisualStudio.VSConstants.S_OK>または<xref:Microsoft.VisualStudio.VSConstants.S_FALSE>を識別することはできません。  
  
 の多くは、 [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] COM 関数が返すか、HRESULT 値が 0 未満か異なる成功コードを返す、[!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)]相互運用機能アセンブリが、メソッドのシグネチャが維持されるように書き込まれました。 すべて[!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)]の相互運用機能のメソッドは、`int`型。 HRESULT 値は変更されず、例外を生成せず、相互運用層を介して渡されます。  
  
 COM 関数が呼び出し元のマネージド メソッドに HRESULT を返すため、呼び出し元のメソッドは、HRESULT を確認し、必要に応じて、例外をスローする必要があります。  
  
## <a name="handling-hresults-returned-to-managed-code-from-com"></a>COM からマネージド コードに返される HRESULT の処理  
 マネージド コードから COM インターフェイスを呼び出す場合は、HRESULT 値を確認し、必要な場合に例外をスローします。 <xref:Microsoft.VisualStudio.ErrorHandler>クラスが含まれています、<xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>に渡されたメソッドは、HRESULT の値に応じて、COM 例外をスローします。  
  
 既定では、<xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>を 0 より小さい値を持つ HRESULT を渡されるたびに、例外をスローします。 このような Hresult が許容される値と、例外をスローする必要がありますに追加 HRESULT の値を渡す必要があります<xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>後の値がテストされます。 テスト対象の HRESULT が明示的に渡された HRESULT 値と一致するかどうか<xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>例外はスローされません。  
  
> [!NOTE]
>  <xref:Microsoft.VisualStudio.VSConstants>クラスに含まれる定数共通 hresult は、たとえば、<xref:Microsoft.VisualStudio.VSConstants.S_OK>と<xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL>、および[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]HRESULT、たとえば、<xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA>と<xref:Microsoft.VisualStudio.VSConstants.VS_E_UNSUPPORTEDFORMAT>します。 <xref:Microsoft.VisualStudio.VSConstants> 用意されています、<xref:Microsoft.VisualStudio.ErrorHandler.Succeeded%2A>と<xref:Microsoft.VisualStudio.ErrorHandler.Failed%2A>メソッドで、COM の SUCCEEDED および FAILED マクロに対応しています  
  
 たとえば、次の関数呼び出しを<xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL>は許容される戻り値が他の HRESULT エラーを表す 0 未満です。  
  
 [!code-csharp[VSSDKHRESULTInformation#1](../snippets/csharp/VS_Snippets_VSSDK/vssdkhresultinformation/cs/vssdkhresultinformationpackage.cs#1)]
 [!code-vb[VSSDKHRESULTInformation#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkhresultinformation/vb/vssdkhresultinformationpackage.vb#1)]  
  
 1 つ以上使用可能な戻り値がある場合への呼び出しリストに追加の HRESULT 値だけできます追加されます<xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>します。  
  
 [!code-csharp[VSSDKHRESULTInformation#2](../snippets/csharp/VS_Snippets_VSSDK/vssdkhresultinformation/cs/vssdkhresultinformationpackage.cs#2)]
 [!code-vb[VSSDKHRESULTInformation#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkhresultinformation/vb/vssdkhresultinformationpackage.vb#2)]  
  
## <a name="returning-hresults-to-com-from-managed-code"></a>マネージド コードから COM に HRESULT を返す  
 例外が発生しない場合は、マネージ コードを返します。<xref:Microsoft.VisualStudio.VSConstants.S_OK>という名前の COM 関数にします。 COM 相互運用では、マネージド コードで厳密に型指定される一般的な例外がサポートされます。 許容できないを受信するメソッドなど、`null`引数がスローされます、<xref:System.ArgumentNullException>します。  
  
 使用することができます、COM に取得するを特定する例外をスローするが、HRESULT がわかって、<xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A>適切な例外をスローするメソッド。 たとえば、非標準のエラーを使用しても動作この<xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA>します。 <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> HRESULT をマップする試行は、厳密に型指定された例外に渡されます。 できない場合は、代わりに一般的な COM 例外をスローします。 最終的には、HRESULT に渡すこと<xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A>という名前の COM 関数をマネージ コードからが返されます。  
  
> [!NOTE]
>  例外によって、パフォーマンスが低下します。例外は、異常なプログラムの条件を示すことを目的としています。 頻繁に発生する条件は、スローされた例外ではなく、インラインで処理をする必要があります。  
  
## <a name="see-also"></a>関連項目  
 [マネージ Vspackage](../misc/managed-vspackages.md)   
 [アンマネージ コードとの相互運用](http://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)   
 [方法: Hresult に例外](http://msdn.microsoft.com/library/610b364b-2761-429d-9c4a-afbc3e66f1b9)   
 [相互運用のための COM コンポーネントの作成](http://msdn.microsoft.com/en-us/7a2c657a-cfef-40f0-bed3-7c2c0ac4abdf)   
 [マネージド VSPackage](../misc/managed-vspackages.md)