---
title: Visual Studio SDK でのイベントの公開 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- events [Visual Studio], exposing
- automation [Visual Studio SDK], exposing events
ms.assetid: 70bbc258-c221-44f8-b0d7-94087d83b8fe
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c08af11ce08cf86948655d01dc5468a3d70ae2fa
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54924307"
---
# <a name="expose-events-in-the-visual-studio-sdk"></a>Visual Studio SDK でイベントを公開します。
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] により、オートメーションを使用してイベントをソースします。 プロジェクトおよびプロジェクト項目のイベントをソースにすることをお勧めします。  
  
 イベントからの automation のコンシューマーによって取得、<xref:EnvDTE.DTEClass.Events%2A>オブジェクトまたは<xref:EnvDTE.DTEClass.GetObject%2A>(たとえば、 `GetObject("EventObjectName")`)。 環境は`IDispatch::Invoke`を使用して、`DISPATCH_METHOD`または`DISPATCH_PROPERTYGET`フラグをイベントを返します。  
  
 次のプロセスでは、VSPackage に固有のイベントを返す方法について説明します。  
  
1. 環境を起動します。  
  
2. 下にあるすべての値名のレジストリから読み取り、 **Automation**、 **AutomationEvents**、および**AutomationProperties** Vspackage、すべてのストアの名前のキーをテーブルです。  
  
3. この例で、automation、コンシューマーを呼び出す`DTE.Events.AutomationProjectsEvents`または`DTE.Events.AutomationProjectItemsEvents`します。  
  
4. 環境では、テーブルから文字列パラメーターを検索し、対応する VSPackage を読み込みます。  
  
5. 環境は、<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>メソッドの呼び出しでは、この例では、渡された名前を使用して`AutomationProjectsEvents`または`AutomationProjectItemsEvents`します。  
  
6. VSPackage は、メソッドをなどが含まれるルート オブジェクトを作成します。`get_AutomationProjectsEvents`と`get_AutomationProjectItemEvents`をオブジェクトには IDispatch ポインターを返します。  
  
7. 環境では、automation の呼び出しに渡された名前に基づいて、適切なメソッドを呼び出します。  
  
8. `get_`メソッドは、両方を実装する別の IDispatch ベースのイベント オブジェクトを作成、`IConnectionPointContainer`インターフェイスと`IConnectionPoint`インターフェイスを返します、`IDispatchpointer`オブジェクトにします。  
  
   応答する必要がありますにオートメーションを使用してイベントを公開する<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>し、レジストリに追加する文字列。 文字列は、基本的なプロジェクト サンプルでは、 *BscProjectsEvents*と*BscProjectItemsEvents*します。  
  
## <a name="registry-entries-from-the-basic-project-sample"></a>基本的なプロジェクト サンプルからのレジストリ エントリ  
 このセクションでは、オートメーション イベントの値をレジストリに追加する場所を示します。  
  
 **[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0\Packages\\<PkgGUID\>\AutomationEvents]**
  
 **AutomationProjectEvents** = 返します、`AutomationProjectEvents`オブジェクト。  
  
 **AutomationProjectItemEvents** = 返します、`AutomationProjectItemsEvents`オブジェクト。  
  
|名前|型|範囲|説明|  
|----------|----------|-----------|-----------------|  
|既定 (@)|REG_SZ|未使用|使用されません。 ドキュメントのデータ フィールドを使用することができます。|  
|*AutomationProjectsEvents*|REG_SZ|イベント オブジェクトの名前。|キー名のみが関連します。 ドキュメントのデータ フィールドを使用することができます。<br /><br /> この例は、基本的なプロジェクト サンプルから取得されます。|  
|*AutomationProjectItemEvents*|REG_SZ|イベント オブジェクトの名前|キー名のみが関連します。 ドキュメントのデータ フィールドを使用することができます。<br /><br /> この例は、基本的なプロジェクト サンプルから取得されます。|  
  
 Automation、コンシューマーが要求されると、イベント オブジェクトのいずれか、VSPackage をサポートする任意のイベントのメソッドを持つルート オブジェクトを作成します。 環境を適切な呼び出します`get_`このオブジェクトのメソッド。 たとえば場合、`DTE.Events.AutomationProjectsEvents`が呼び出される、`get_AutomationProjectsEvents`ルート オブジェクトのメソッドが呼び出されます。  
  
 ![Visual Studio プロジェクト イベント](../../extensibility/internals/media/projectevents.gif "ProjectEvents")  
イベントのオートメーション モデル  
  
 クラスは、`CProjectEventsContainer`のソース オブジェクトを表す*BscProjectsEvents*と`CProjectItemsEventsContainer`のソース オブジェクトを表す*BscProjectItemsEvents*します。  
  
 ほとんどの場合は、イベントのほとんどのオブジェクトがフィルター オブジェクトがかかるため、イベント要求ごとに新しいオブジェクトを返す必要があります。 イベントを起動するときは、イベント ハンドラーが呼び出されていることを確認するには、このフィルターを確認します。  
  
 *AutomationEvents.h*と*AutomationEvents.cpp*宣言と次の表に、クラスの実装を含めることができます。  
  
|クラス|説明|  
|-----------|-----------------|  
|`CAutomationEvents`|取得したイベントのルート オブジェクトを実装して、`DTE.Events`オブジェクト。|  
|`CProjectsEventsContainer` および `CProjectItemsEventsContainer`|対応するイベントを発生させるイベント ソースのオブジェクトを実装します。|  
  
 次のコード例では、イベント オブジェクトの要求に応答する方法を示します。  
  
```cpp  
STDMETHODIMP CVsPackage::GetAutomationObject(  
    /* [in]  */ LPCOLESTR       pszPropName,   
    /* [out] */ IDispatch **    ppIDispatch)  
{  
    ExpectedPtrRet(ppIDispatch);  
    *ppIDispatch = NULL;  
  
    if (_wcsicmp(pszPropName, g_wszAutomationProjects) == 0)   
        //Is the requested name our Projects object?  
    {  
        return GetAutomationProjects(ppIDispatch);  
        // Gets our Projects object.  
    }  
    else if (_wcsicmp(pszPropName, g_wszAutomationProjectsEvents) == 0)  
        //Is the requested name our ProjectsEvents object?  
    {  
        return CAutomationEvents::GetAutomationEvents(ppIDispatch);  
          // Gets our ProjectEvents object.  
    }  
    else if (_wcsicmp(pszPropName, g_wszAutomationProjectItemsEvents) == 0)  //Is the requested name our ProjectsItemsEvents object?  
    {  
        return CAutomationEvents::GetAutomationEvents(ppIDispatch);  
          // Gets our ProjectItemsEvents object.  
    }  
    return E_INVALIDARG;  
}  
```  
  
 上記のコードで`g_wszAutomationProjects`、プロジェクト コレクションの名前を指定します (*FigProjects*)、 `g_wszAutomationProjectsEvents` (*FigProjectsEvents*) と`g_wszAutomationProjectItemsEvents`(*FigProjectItemEvents*) プロジェクト イベントの名前は、プロジェクト項目のソースは、VSPackage 実装するイベントです。  
  
 イベント オブジェクトが同じの一元化された場所から取得した、`DTE.Events`オブジェクト。 これにより、すべてのイベント オブジェクトはようにグループ化、エンドユーザーは、特定のイベントを検索する全体オブジェクト モデルを参照する必要はありません。 これによりシステム全体のイベントのコードを実装する必要はなく、特定の VSPackage オブジェクトを指定できますも。 ただし、エンドユーザーのユーザー見つける必要がありますのイベント、`ProjectItem`インターフェイス、明確ではありません直後から、そのイベント オブジェクトが取得されます。  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>   
