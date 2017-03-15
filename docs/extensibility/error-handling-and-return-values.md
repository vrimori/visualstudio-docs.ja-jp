---
title: "エラー処理と戻り値 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- errors [Visual Studio SDK], handling
- error handling
- return values
ms.assetid: b2d9079d-39a6-438a-8010-290056694b5c
caps.latest.revision: 14
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
ms.openlocfilehash: c30c795363738b5715bc6d5c928ba8553d01210b
ms.lasthandoff: 02/22/2017

---
# <a name="error-handling-and-return-values"></a>エラー処理と戻り値
Vspackage と COM のエラーと同じアーキテクチャを使用します。 `SetErrorInfo`と`GetErrorInfo`関数は、Win32 アプリケーション プログラミング インターフェイス (API) の一部です。 統合開発環境 (IDE) 内のすべての VSPackage を呼び出せるこれら豊富なエラー情報を記録するグローバルの Win32 Api エラー通知を受信するときにです。 [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)]エラー情報を管理する相互運用機能アセンブリを提供します。  
  
## <a name="interop-methods"></a>相互運用メソッド  
 IDE は、メソッドを提供しやすくするため、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>、Win32 Api を呼び出す代わりに使用する</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>。 マネージ コードで<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>。</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>を使用してください。 エラー時に`HRESULT`レベルのエラー メッセージを表示できる場所に到着する (これは、多くの場合、オブジェクトを実装する、<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>コマンド ハンドラー)、IDE は、別の方法を使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A>、適切なメッセージ ボックスを表示します</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A></xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>。 マネージ コードの使用中、<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A>メソッド</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A>。  
  
 COM オブジェクトの通常の実装を VSPackage の実行者、`ISupportErrorInfo`です。 `ISupportErrorInfo`インターフェイスにより、詳細なエラー情報は、呼び出しチェーンを垂直方向に移動できます。 スレッド間またはプロセス間で使用されるオブジェクトをサポートする必要があります`ISupportErrorInfo`に呼び出し元に豊富なエラー情報が正しくマーシャ リングすることを確認します。  
  
 VSPackages に関連して、エディター ファクトリ、エディター、階層も含め、IDE の拡張に関連するサービスを提供し、すべてのオブジェクトには、豊富なエラー情報をサポートする必要があります。 IDE には、これらの VSPackage オブジェクトを実装するのには不要、 `ISupportErrorInfo`、常にお勧めします。  
  
 IDE がエラー情報を報告してのユーザーに表示を担当[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]されるたびに、 `HRESULT` IDE に反映されます。 IDE が作成するためのメカニズムでも`ErrorInfo`オブジェクトです。  
  
## <a name="general-guidelines"></a>一般的なガイドライン  
 使用することができます、<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>と<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A>設定および VSPackage 実装もに内部エラーを報告するメソッド</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>。 ただし、一般的な規則としては、VSPackage でのエラー メッセージを処理するための次のガイドラインに従います。  
  
-   実装`ISupportErrorInfo`VSPackage COM オブジェクトにします。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>。</xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>を実装するオブジェクトのメソッド</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>を呼び出すためのメカニズムを報告するエラーを作成します。  
  
-   IDE をユーザーにエラーを表示させる、<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A>メソッド</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A>。  
  
## <a name="error-information-in-the-ide"></a>IDE でのエラー情報  
 次のルールでエラーに関する情報を処理する方法を指定して、 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE。  
  
-   ユーザーに古いエラー情報が表示されないことを保証するために防御戦略の関数を呼び出すと、<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A>まずメソッドを呼び出して、<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>メソッド</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A>。 渡す`null`新しいエラー情報を設定が何もするを呼び出す前に、キャッシュされたエラー メッセージをクリアします。  
  
-   エラー メッセージを直接報告しない関数を呼び出すことだけが、<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>メソッドの場合は、エラーを返す、 `HRESULT`</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> 。 オフにすることは、`ErrorInfo`関数または<xref:Microsoft.VisualStudio.VSConstants.S_OK>.</xref:Microsoft.VisualStudio.VSConstants.S_OK>を返すときにエントリを このルールの唯一の例外の呼び出しがエラーを返す場合は、`HRESULT`から受信側パーティを明示的にリカバリか無視してかまいません。  
  
-   エラーを明示的に無視できる`HRESULT`<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A><xref:Microsoft.VisualStudio.VSConstants.S_OK></xref:Microsoft.VisualStudio.VSConstants.S_OK>メソッド</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>を呼び出す必要があります。 それ以外の場合、`ErrorInfo`別のパーティが自身を指定せず、エラーを生成するときに、オブジェクトを誤って使用する場合があります`ErrorInfo`します。  
  
-   エラーが発生したすべてのメソッド`HRESULT`を呼び出すことをお勧めします<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>豊富なエラー情報を提供するメソッド</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>。 場合、返された`HRESULT`は特殊な`FACILITY_ITF`エラーし、メソッドが適切なを提供する必要な`ErrorInfo`オブジェクトです。 返されたエラーは、標準的なシステム エラーがある場合 (たとえば、 <xref:Microsoft.VisualStudio.VSConstants.E_OUTOFMEMORY>、 <xref:Microsoft.VisualStudio.VSConstants.E_ABORT>、 <xref:Microsoft.VisualStudio.VSConstants.E_INVALIDARG>、 <xref:Microsoft.VisualStudio.VSConstants.E_UNEXPECTED>、) 明示的に呼び出さずに、エラー コードを制御することができます、<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>メソッド。</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> </xref:Microsoft.VisualStudio.VSConstants.E_UNEXPECTED> </xref:Microsoft.VisualStudio.VSConstants.E_INVALIDARG> </xref:Microsoft.VisualStudio.VSConstants.E_ABORT> </xref:Microsoft.VisualStudio.VSConstants.E_OUTOFMEMORY> 。 防御的なコーディング戦略として、エラーが発生したときに`HRESULT`(エラー)、システムを含む常に呼び出して、<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>でいずれかのメソッド`ErrorInfo`をより詳細に、エラーを説明または`null`</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>。  
  
-   障害が発生したから受信した情報を渡す必要があります別の呼び出しによって発生したエラーを返すすべての関数を呼び出す、`HRESULT`を変更しなくても、`ErrorInfo`オブジェクトです。  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget></xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>   
 [SetErrorInfo (コンポーネント オートメーション)](http://msdn.microsoft.com/en-us/8eaacfac-fc37-4eaa-870b-10b99d598d66)   
 [GetErrorInfo](http://msdn.microsoft.com/en-us/03317526-8c4f-4173-bc10-110c8112676a)   
 [ISupportErrorInfo インターフェイス](http://msdn.microsoft.com/en-us/42d33066-36b4-4a5b-aa5d-46682e560f32)
