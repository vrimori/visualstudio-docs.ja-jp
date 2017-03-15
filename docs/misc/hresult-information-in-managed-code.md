---
title: "マネージ コードの HRESULT 情報 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "HResult, マネージ VSPackage"
  - "VSPackage, HRESULT 情報"
ms.assetid: 0795ee94-17a8-4327-bf57-27cd5e312a4c
caps.latest.revision: 29
caps.handback.revision: 29
manager: "douge"
---
# マネージ コードの HRESULT 情報
マネージ コードと COM の相互作用によって、HRESULT 戻り値が検出されたときに問題が発生する可能性があります。  
  
 COM インターフェイスでは、HRESULT 戻り値が次の役割を果たします。  
  
-   エラー情報を提供します \(<xref:Microsoft.VisualStudio.VSConstants.E_INVALIDARG> など\)。  
  
-   通常のプログラムの動作に関するステータス情報を提供します。  
  
 COM がマネージ コードへの呼び出しを行うと、HRESULT によって次の問題が発生する可能性があります。  
  
-   ゼロ未満の HRESULT 値 \(エラー コード\) を返す COM 関数によって、例外が生成されます。  
  
-   <xref:Microsoft.VisualStudio.VSConstants.S_OK> や <xref:Microsoft.VisualStudio.VSConstants.S_FALSE> などの 2 つ以上のさまざまな成功コードを定期的に返す COM メソッドを識別することはできません。  
  
 [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] COM 関数の多くは、ゼロ未満の HRESULT 値を返すか、異なる成功コードを返すため、メソッドのシグネチャが保持されるように [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] 相互運用機能アセンブリが書き込まれています。 すべての [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] 相互運用メソッドは、`int` 型です。 HRESULT 値は変更されず、例外を生成せず、相互運用層を介して渡されます。  
  
 COM 関数が呼び出し元のマネージ メソッドに HRESULT を返すため、呼び出し元のメソッドは、HRESULT を確認し、必要に応じて、例外をスローする必要があります。  
  
## COM からマネージ コードに返される HRESULT の処理  
 マネージ コードから COM インターフェイスを呼び出す場合は、HRESULT 値を確認し、必要な場合に例外をスローします。 渡された HRESULT の値に応じて、<xref:Microsoft.VisualStudio.ErrorHandler> クラスには COM 例外をスローする <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> メソッドが含まれます。  
  
 既定では、<xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> は、0 より小さい値を持つ HRESULT を渡されるたびに例外をスローします。 このような HRESULT が許容される値であり、例外をスローする必要がない場合は、値のテスト後に追加 HRESULT の値を <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> に渡す必要があります。 テスト対象の HRESULT が、<xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> に明示的に渡される HRESULT 値と一致する場合、例外はスローされません。  
  
> [!NOTE]
>  <xref:Microsoft.VisualStudio.VSConstants> クラスには、共通 HRESULT \(<xref:Microsoft.VisualStudio.VSConstants.S_OK> や <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL> など\) および [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] HRESULT \(<xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA> や <xref:Microsoft.VisualStudio.VSConstants.VS_E_UNSUPPORTEDFORMAT> など\) の定数が含まれます。 また、<xref:Microsoft.VisualStudio.VSConstants> には、COM の SUCCEEDED および FAILED マクロに対応する <xref:Microsoft.VisualStudio.ErrorHandler.Succeeded%2A> および <xref:Microsoft.VisualStudio.ErrorHandler.Failed%2A> メソッドが用意されています。  
  
 たとえば、<xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL> が許容可能な戻り値であり、ゼロ未満の他の HRESULT がエラーを表す次の関数呼び出しがあるとします。  
  
 [!code-vb[VSSDKHRESULTInformation#1](../extensibility/internals/codesnippet/VisualBasic/hresult-information-in-managed-code_1.vb)]
 [!code-cs[VSSDKHRESULTInformation#1](../extensibility/internals/codesnippet/CSharp/hresult-information-in-managed-code_1.cs)]  
  
 許容可能な戻り値が複数ある場合は、<xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> への呼び出しの一覧にのみ追加の HRESULT 値を追加することができます。  
  
 [!code-vb[VSSDKHRESULTInformation#2](../extensibility/internals/codesnippet/VisualBasic/hresult-information-in-managed-code_2.vb)]
 [!code-cs[VSSDKHRESULTInformation#2](../extensibility/internals/codesnippet/CSharp/hresult-information-in-managed-code_2.cs)]  
  
## マネージ コードから COM に HRESULT を返す  
 例外が発生しない場合、マネージ コードは呼び出し元の COM 関数に <xref:Microsoft.VisualStudio.VSConstants.S_OK> を返します。 COM 相互運用では、マネージ コードで厳密に型指定される一般的な例外がサポートされます。 たとえば、受け入れられない `null` 引数を受け取るメソッドは、<xref:System.ArgumentNullException> をスローします。  
  
 スローする例外が不明であり、COM に戻す HRESULT がわかっている場合は、<xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> メソッドを使用して、適切な例外をスローすることができます。 これは、<xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA> などの非標準のエラーでも機能します。<xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> では、渡された HRESULT を厳密に型指定された例外にマップすることを試みます。 できない場合は、代わりに一般的な COM 例外をスローします。 最終的な結果では、マネージ コードから <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> に渡す HRESULT が呼び出し元の COM 関数に返されます。  
  
> [!NOTE]
>  例外によって、パフォーマンスが低下します。例外は、異常なプログラムの条件を示すことを目的としています。 頻繁に発生する条件は、スローされた例外ではなく、インラインで処理をする必要があります。  
  
## 参照  
 [マネージ VSPackage](../misc/managed-vspackages.md)   
 [アンマネージ コードとの相互運用](../Topic/Interoperating%20with%20Unmanaged%20Code.md)   
 [方法: HRESULT に例外を割り当てる](../Topic/How%20to:%20Map%20HRESULTs%20and%20Exceptions.md)   
 [相互運用性を得るための COM コンポーネントの作成](http://msdn.microsoft.com/ja-jp/7a2c657a-cfef-40f0-bed3-7c2c0ac4abdf)   
 [マネージ VSPackage](../misc/managed-vspackages.md)