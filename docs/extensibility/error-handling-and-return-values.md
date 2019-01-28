---
title: エラー処理と戻り値 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- errors [Visual Studio SDK], handling
- error handling
- return values
ms.assetid: b2d9079d-39a6-438a-8010-290056694b5c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e524939e6fe17dfdaafc4ad4f26d5978174f3352
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54921922"
---
# <a name="error-handling-and-return-values"></a>エラー処理と戻り値
Vspackage と COM のエラーと同じアーキテクチャを使用します。 `SetErrorInfo`と`GetErrorInfo`関数は、Win32 アプリケーション プログラミング インターフェイス (API) の一部です。 統合開発環境 (IDE) ですべての VSPackage できますこれらグローバル Win32 Api を呼び出して詳細なエラー情報を記録エラー通知を受信するときにします。 [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)]エラー情報を管理する相互運用機能アセンブリを提供します。  
  
## <a name="interop-methods"></a>相互運用メソッド  
 IDE は、メソッドを提供、便宜上、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>、Win32 Api を呼び出す代わりに使用します。 マネージ コードの使用で<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>します。 ときにエラー`HRESULT`エラー メッセージが表示されるレベルに到達する (これは、多くの場合、オブジェクトを実装する、<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>コマンド ハンドラー)、IDE は、別の方法を使用して<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A>、適切なメッセージ ボックスを表示します。 マネージ コードの使用、<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A>メソッド。  
  
 COM オブジェクトの通常の実装を VSPackage の実行者、`ISupportErrorInfo`します。 `ISupportErrorInfo`インターフェイスにより、詳細なエラー情報は、呼び出しチェーンを垂直方向に移動できます。 プロセス間またはスレッド間で使用されるオブジェクトをサポートする必要があります`ISupportErrorInfo`に詳細なエラー情報が、呼び出し元に正しくマーシャ リングすることを確認します。  
  
 Vspackage に関連して、エディター ファクトリ、エディター、階層など、IDE の拡張に関連するサービスを提供し、すべてのオブジェクトには、詳細なエラー情報をサポートする必要があります。 IDE でこれらを実装する VSPackage のオブジェクトが必要ありません`ISupportErrorInfo`、常にお勧めします。  
  
 IDE がエラー情報をレポートとのユーザーに表示する責任を負います[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]たびに、`HRESULT`が IDE に反映されます。 IDE が作成するためのメカニズムでも`ErrorInfo`オブジェクト。  
  
## <a name="general-guidelines"></a>一般的なガイドライン  
 使用することができます、<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>と<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A>メソッドを設定し、VSPackage の実装も内部的なエラーを報告します。 ただし、一般的な規則として、VSPackage でのエラー メッセージを処理するためのこれらのガイドラインに従います。  
  
-   実装`ISupportErrorInfo`VSPackage の COM オブジェクト。  
  
-   エラー レポートを呼び出すための機構を作成、<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>メソッドを実装するオブジェクトで<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>します。  
  
-   IDE をユーザーにエラーを表示できるように、<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A>メソッド。  
  
## <a name="error-information-in-the-ide"></a>IDE のエラー情報  
 次の規則にエラー情報を処理する方法を示すため、 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE。  
  
-   関数の呼び出しのユーザーに古いエラー情報が表示されないことを保証するために防御的な戦略、<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A>メソッドを呼び出す必要があります最初、<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>メソッド。 渡す`null`エラー情報の新しい設定何かを呼び出す前に、キャッシュされたエラー メッセージをクリアします。  
  
-   エラー メッセージを直接報告しない関数を呼び出すのみ、<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>メソッドの場合はエラーを返す、`HRESULT`します。 オフにすることは、`ErrorInfo`関数またはを返すときに、エントリに<xref:Microsoft.VisualStudio.VSConstants.S_OK>します。 このルールの唯一の例外が呼び出しでエラーが返される`HRESULT`からは、受信側パーティに明示的に回復またはできるを無視します。  
  
-   明示的にエラーを無視するすべての当事者`HRESULT`呼び出す必要があります、<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>メソッド<xref:Microsoft.VisualStudio.VSConstants.S_OK>します。 それ以外の場合、`ErrorInfo`別のパーティが独自に提供することがなくエラーを生成するときに、オブジェクトを誤って使用する場合があります`ErrorInfo`します。  
  
-   エラーが発生したすべてのメソッド`HRESULT`を呼び出すことが推奨されます、<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>詳細なエラー情報を提供するメソッド。 場合、返された`HRESULT`は特殊な`FACILITY_ITF`エラー、その後、メソッドは、適切なを指定する必要が`ErrorInfo`オブジェクト。 返されたエラーは、標準のシステム エラーがある場合 (たとえば、 <xref:Microsoft.VisualStudio.VSConstants.E_OUTOFMEMORY>、 <xref:Microsoft.VisualStudio.VSConstants.E_ABORT>、 <xref:Microsoft.VisualStudio.VSConstants.E_INVALIDARG>、 <xref:Microsoft.VisualStudio.VSConstants.E_UNEXPECTED>、。) すると、明示的に呼び出さずに、エラー コードを返すことができます、<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>メソッド。 防御的なコーディング戦略として、エラーが発生したときに`HRESULT`常に呼び出します (エラー)、システムを含む、<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>メソッドは、いずれかで`ErrorInfo`より詳細に、エラーを説明または`null`します。  
  
-   別の呼び出しによって発生したエラーは、障害が発生したから受信した情報を渡す必要がありますが返すすべての関数を呼び出す、`HRESULT`を変更しなくても、`ErrorInfo`オブジェクト。  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>   
 [SetErrorInfo (コンポーネント オートメーション)](/previous-versions/windows/desktop/api/oleauto/nf-oleauto-seterrorinfo)   
 [GetErrorInfo](/previous-versions/windows/desktop/api/oleauto/nf-oleauto-geterrorinfo)   
 [ISupportErrorInfo インターフェイス](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-isupporterrorinfo)
