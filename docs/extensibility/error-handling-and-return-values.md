---
title: エラー処理と戻り値 |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- errors [Visual Studio SDK], handling
- error handling
- return values
ms.assetid: b2d9079d-39a6-438a-8010-290056694b5c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6cfbeef2de041cfd71fbf163d7860d903a6cb59e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="error-handling-and-return-values"></a>エラー処理と戻り値
Vspackage と COM のエラーと同じアーキテクチャを使用します。 `SetErrorInfo`と`GetErrorInfo`関数は、Win32 アプリケーション プログラミング インターフェイス (API) の一部です。 統合開発環境 (IDE) で、VSPackage を呼び出せるこれら豊富なエラー情報を記録するグローバルの Win32 Api エラー通知を受信するときにです。 [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)]エラー情報を管理する相互運用機能アセンブリを提供します。  
  
## <a name="interop-methods"></a>相互運用メソッド  
 IDE が、メソッドを提供する、便宜上、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>、Win32 Api を呼び出す代わりに使用します。 マネージ コードの使用中で<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>です。 ときにエラー`HRESULT`エラー メッセージを表示するか、レベルに到着する (これは、多くの場合、オブジェクトを実装する、<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>コマンド ハンドラー)、IDE は、別の方法を使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A>、適切なメッセージ ボックスを表示します。 マネージ コードの使用中、<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A>メソッドです。  
  
 COM オブジェクトの通常の実装を VSPackage の実行者、`ISupportErrorInfo`です。 `ISupportErrorInfo`インターフェイスにより、詳細なエラー情報は、呼び出しチェーンを垂直方向に移動できます。 スレッド間またはプロセス間で使用されるオブジェクトをサポートする必要があります`ISupportErrorInfo`に詳細なエラー情報が正しく、呼び出し元にマーシャ リングすることを確認します。  
  
 Vspackage に関連して、エディター ファクトリ、エディター、階層も含め、IDE の拡張に関係するサービスを提供し、すべてのオブジェクトには、詳細なエラー情報をサポートする必要があります。 中、IDE はこれらの VSPackage オブジェクトを実装する必要はありません`ISupportErrorInfo`、これは常にことをお勧めします。  
  
 IDE がエラー情報を報告しのユーザーに表示を担当[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]されるたびに、`HRESULT`は IDE に反映されます。 IDE が作成するためのメカニズムでも`ErrorInfo`オブジェクト。  
  
## <a name="general-guidelines"></a>一般的なガイドライン  
 使用することができます、<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>と<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A>メソッドを設定し、VSPackage の実装を同様の内部エラーを報告します。 ただし、一般的な規則として、VSPackage でのエラー メッセージを処理するためのこれらのガイドラインに従います。  
  
-   実装`ISupportErrorInfo`VSPackage の COM オブジェクトでします。  
  
-   呼び出すメカニズムを報告するエラーを作成、<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>メソッドを実装するオブジェクトで<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>です。  
  
-   IDE をユーザーにエラーを表示させる、<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A>メソッドです。  
  
## <a name="error-information-in-the-ide"></a>IDE でのエラー情報  
 次の規則にエラー情報を処理する方法を指定して、 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE します。  
  
-   古いエラー情報が、ユーザーに報告されていないことを保証するために防御戦略関数を呼び出すと、<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A>メソッドを呼び出す必要があります最初、<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>メソッドです。 渡す`null`新しいエラー情報を設定が何もするを呼び出す前に、キャッシュされたエラー メッセージをクリアします。  
  
-   エラー メッセージを直接報告しない関数はのみを呼び出す、<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>メソッドの場合はエラーを返す、`HRESULT`です。 オフにすることは、`ErrorInfo`関数またはを返すときに、エントリに<xref:Microsoft.VisualStudio.VSConstants.S_OK>です。 このルールの唯一の例外が呼び出しには、エラーが返される`HRESULT`は、受信側パーティに明示的に回復またはできる安全に無視するからです。  
  
-   明示的にエラーを無視するすべての当事者`HRESULT`呼び出す必要があります、<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>メソッドを<xref:Microsoft.VisualStudio.VSConstants.S_OK>です。 それ以外の場合、`ErrorInfo`別のパーティが独自に提供せず、エラーを生成するときに、オブジェクトを誤って使用する場合があります`ErrorInfo`です。  
  
-   エラーが発生したすべてのメソッド`HRESULT`を呼び出すことをお勧め、<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>豊富なエラー情報を提供するメソッド。 場合、返された`HRESULT`は特殊な`FACILITY_ITF`エラー、メソッドは、適切なを指定する必要は`ErrorInfo`オブジェクト。 返されたエラーは、標準のシステム エラー場合、(たとえば、 <xref:Microsoft.VisualStudio.VSConstants.E_OUTOFMEMORY>、 <xref:Microsoft.VisualStudio.VSConstants.E_ABORT>、 <xref:Microsoft.VisualStudio.VSConstants.E_INVALIDARG>、 <xref:Microsoft.VisualStudio.VSConstants.E_UNEXPECTED>、しにします。) を明示的に呼び出さずに、エラー コードを返します、<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>メソッドです。 防御的なコーディング戦略として、エラーが発生したときに`HRESULT`常に呼び出します (エラー)、システムを含む、<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>でいずれかのメソッド`ErrorInfo`詳しくは、エラーを示すまたは`null`です。  
  
-   別の呼び出しによって発生したエラーは、障害が発生したから受信した情報を渡す必要がありますを返すすべての関数を呼び出す、`HRESULT`を変更しなくても、`ErrorInfo`オブジェクト。  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>   
 [SetErrorInfo (コンポーネント オートメーション)](http://msdn.microsoft.com/en-us/8eaacfac-fc37-4eaa-870b-10b99d598d66)   
 [GetErrorInfo](http://msdn.microsoft.com/en-us/03317526-8c4f-4173-bc10-110c8112676a)   
 [ISupportErrorInfo インターフェイス](http://msdn.microsoft.com/en-us/42d33066-36b4-4a5b-aa5d-46682e560f32)