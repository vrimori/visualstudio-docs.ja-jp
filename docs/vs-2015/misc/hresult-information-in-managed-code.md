---
title: マネージ コードの HRESULT 情報 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
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
ms.openlocfilehash: b629f856bcdba13523c094b5d3fd32b6848ec23f
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49256075"
---
# <a name="hresult-information-in-managed-code"></a>マネージ コードの HRESULT 情報
マネージド コードと COM の相互作用によって、HRESULT 戻り値が検出されたときに問題が発生する可能性があります。  
  
 COM インターフェイスでは、HRESULT 戻り値が次の役割を果たします。  
  
-   エラー情報を提供します (<xref:Microsoft.VisualStudio.VSConstants.E_INVALIDARG> など)。  
  
-   通常のプログラムの動作に関するステータス情報を提供します。  
  
 COM がマネージド コードへの呼び出しを行うと、HRESULT によって次の問題が発生する可能性があります。  
  
-   ゼロ未満の HRESULT 値 (エラー コード) を返す COM 関数によって、例外が生成されます。  
  
-   <xref:Microsoft.VisualStudio.VSConstants.S_OK> や <xref:Microsoft.VisualStudio.VSConstants.S_FALSE> などの 2 つ以上のさまざまな成功コードを定期的に返す COM メソッドを識別することはできません。  
  
 [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] COM 関数の多くは、ゼロ未満の HRESULT 値を返すか、異なる成功コードを返すため、メソッドのシグネチャが保持されるように [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] 相互運用機能アセンブリが書き込まれています。 すべての [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] 相互運用メソッドは、 `int` 型です。 HRESULT 値は変更されず、例外を生成せず、相互運用層を介して渡されます。  
  
 COM 関数が呼び出し元のマネージド メソッドに HRESULT を返すため、呼び出し元のメソッドは、HRESULT を確認し、必要に応じて、例外をスローする必要があります。  
  
## <a name="handling-hresults-returned-to-managed-code-from-com"></a>COM からマネージド コードに返される HRESULT の処理  
 マネージド コードから COM インターフェイスを呼び出す場合は、HRESULT 値を確認し、必要な場合に例外をスローします。 渡された HRESULT の値に応じて、<xref:Microsoft.VisualStudio.ErrorHandler> クラスには COM 例外をスローする <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> メソッドが含まれます。  
  
 既定では、<xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> は、0 より小さい値を持つ HRESULT を渡されるたびに例外をスローします。 このような HRESULT が許容される値であり、例外をスローする必要がない場合は、値のテスト後に追加 HRESULT の値を <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> に渡す必要があります。 テスト対象の HRESULT が、<xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> に明示的に渡される HRESULT 値と一致する場合、例外はスローされません。  
  
> [!NOTE]
>  <xref:Microsoft.VisualStudio.VSConstants>クラスに含まれる定数共通 hresult は、たとえば、<xref:Microsoft.VisualStudio.VSConstants.S_OK>と<xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL>、および[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]HRESULT、たとえば、<xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA>と<xref:Microsoft.VisualStudio.VSConstants.VS_E_UNSUPPORTEDFORMAT>します。 また、<xref:Microsoft.VisualStudio.VSConstants> には、COM の SUCCEEDED および FAILED マクロに対応する <xref:Microsoft.VisualStudio.ErrorHandler.Succeeded%2A> および <xref:Microsoft.VisualStudio.ErrorHandler.Failed%2A> メソッドが用意されています。  
  
 たとえば、<xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL> が許容可能な戻り値であり、ゼロ未満の他の HRESULT がエラーを表す次の関数呼び出しがあるとします。  
  
 [!code-csharp[VSSDKHRESULTInformation#1](../snippets/csharp/VS_Snippets_VSSDK/vssdkhresultinformation/cs/vssdkhresultinformationpackage.cs#1)]
 [!code-vb[VSSDKHRESULTInformation#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkhresultinformation/vb/vssdkhresultinformationpackage.vb#1)]  
  
 許容可能な戻り値が複数ある場合は、<xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> への呼び出しの一覧にのみ追加の HRESULT 値を追加することができます。  
  
 [!code-csharp[VSSDKHRESULTInformation#2](../snippets/csharp/VS_Snippets_VSSDK/vssdkhresultinformation/cs/vssdkhresultinformationpackage.cs#2)]
 [!code-vb[VSSDKHRESULTInformation#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkhresultinformation/vb/vssdkhresultinformationpackage.vb#2)]  
  
## <a name="returning-hresults-to-com-from-managed-code"></a>マネージド コードから COM に HRESULT を返す  
 例外が発生しない場合、マネージド コードは呼び出し元の COM 関数に <xref:Microsoft.VisualStudio.VSConstants.S_OK> を返します。 COM 相互運用では、マネージド コードで厳密に型指定される一般的な例外がサポートされます。 たとえば、受け入れられない `null` 引数を受け取るメソッドは、<xref:System.ArgumentNullException> をスローします。  
  
 スローする例外が不明であり、COM に戻す HRESULT がわかっている場合は、<xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> メソッドを使用して、適切な例外をスローすることができます。 これは、<xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA> などの非標準のエラーでも機能します。 <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> では、渡された HRESULT を厳密に型指定された例外にマップすることを試みます。 できない場合は、代わりに一般的な COM 例外をスローします。 最終的な結果では、マネージド コードから <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> に渡す HRESULT が呼び出し元の COM 関数に返されます。  
  
> [!NOTE]
>  例外によって、パフォーマンスが低下します。例外は、異常なプログラムの条件を示すことを目的としています。 頻繁に発生する条件は、スローされた例外ではなく、インラインで処理をする必要があります。  
  
## <a name="see-also"></a>関連項目  
 [マネージ Vspackage](../misc/managed-vspackages.md)   
 [アンマネージ コードとの相互運用](http://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)   
 [方法: Hresult に例外](http://msdn.microsoft.com/library/610b364b-2761-429d-9c4a-afbc3e66f1b9)   
 [相互運用のための COM コンポーネントの作成](http://msdn.microsoft.com/en-us/7a2c657a-cfef-40f0-bed3-7c2c0ac4abdf)   
 [マネージド VSPackage](../misc/managed-vspackages.md)