---
title: "Visual Studio SDK 内のイベントを公開する |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- events [Visual Studio], exposing
- automation [Visual Studio SDK], exposing events
ms.assetid: 70bbc258-c221-44f8-b0d7-94087d83b8fe
caps.latest.revision: "16"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 74a9ff54d14b6212d0fc484acd2bd25fad18bb87
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="exposing-events-in-the-visual-studio-sdk"></a>Visual Studio SDK 内のイベントを公開します。
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]により、オートメーションを使用してイベントをソースします。 プロジェクトとプロジェクト項目のイベントをソースにすることをお勧めします。  
  
 イベントからオートメーション コンシューマーによって取得、<xref:EnvDTE.DTEClass.Events%2A>オブジェクトまたは<xref:EnvDTE.DTEClass.GetObject%2A>("EventObjectName") です。 環境の呼び出し`IDispatch::Invoke`を使用して、`DISPATCH_METHOD`または`DISPATCH_PROPERTYGET`フラグをイベントを返します。  
  
 次のプロセスでは、VSPackage に固有のイベントを返す方法について説明します。  
  
1.  環境を起動します。  
  
2.  すべての Vspackage、オートメーション、AutomationEvents AutomationProperties の各キー下にあるすべての値の名前をレジストリから読み取るし、テーブルでこれらの名前を格納します。  
  
3.  オートメーション コンシューマーを呼び出すと、この例では`DTE.Events.AutomationProjectsEvents`または`DTE.Events.AutomationProjectItemsEvents`です。  
  
4.  環境では、テーブル内の文字列パラメーターを検索し、対応する VSPackage を読み込みます。  
  
5.  環境の呼び出し、<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>呼び出しで; AutomationProjectsEvents または AutomationProjectItemsEvents この例では、名前を使用してメソッドが渡されます。  
  
6.  VSPackage をなどのメソッドを持つルート オブジェクトを作成する`get_AutomationProjectsEvents`と`get_AutomationProjectItemEvents`し、オブジェクトを IDispatch ポインターを返します。  
  
7.  環境では、オートメーションの呼び出しに渡された名前に基づいて、適切なメソッドを呼び出します。  
  
8.  `get_`メソッドを実装する別の IDispatch ベースのイベント オブジェクトを作成、`IConnectionPointContainer`インターフェイスおよび`IConnectionPoint`インターフェイスし、オブジェクトへの IDispatchpointer を返します。  
  
 オートメーションを使用してイベントを公開するために応答する必要があります<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>し、レジストリに追加する文字列。 基本的なプロジェクト サンプルでは、文字列は、"BscProjectsEvents"および"BscProjectItemsEvents"です。  
  
## <a name="registry-entries-from-the-basic-project-sample"></a>基本的なプロジェクトのサンプルからのレジストリ エントリ  
 このセクションでは、オートメーション イベント値をレジストリに追加する場所を示します。  
  
 [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0\Packages\\< PkgGUID\>\AutomationEvents]  
  
 「AutomationProjectEvents オブジェクトを返します AutomationProjectEvents「=」」  
  
 「AutomationProjectItemsEvents オブジェクトを返します AutomationProjectItemEvents「=」」  
  
|name|型|範囲|説明|  
|----------|----------|-----------|-----------------|  
|既定の (@)|REG_SZ|未使用|使用されません。 ドキュメントについては、データ フィールドを使用できます。|  
|AutomationProjectsEvents|REG_SZ|イベント オブジェクトの名前です。|キー名のみが関連します。 ドキュメントについては、データ フィールドを使用できます。<br /><br /> この例は、基本的なプロジェクトのサンプルから取得されます。|  
|AutomationProjectItemEvents|REG_SZ|イベント オブジェクトの名前|キー名のみが関連します。 ドキュメントについては、データ フィールドを使用できます。<br /><br /> この例は、基本的なプロジェクトのサンプルから取得されます。|  
  
 オートメーション コンシューマーによって要求されると、イベント オブジェクトのいずれか、VSPackage をサポートする任意のイベントのメソッドを持つルート オブジェクトを作成します。 環境を適切な呼び出します`get_`このオブジェクトのメソッドです。 たとえば場合、`DTE.Events.AutomationProjectsEvents`が呼び出されたが、`get_AutomationProjectsEvents`ルート オブジェクトのメソッドが呼び出されます。  
  
 ![Visual Studio プロジェクト イベント](../../extensibility/internals/media/projectevents.gif "ProjectEvents")  
イベントのオートメーション モデル  
  
 クラス`CProjectEventsContainer`BscProjectsEvents、用のソース オブジェクトを表すときに`CProjectItemsEventsContainer`BscProjectItemsEvents のソース オブジェクトを表します。  
  
 ほとんどの場合は、ほとんどのイベント オブジェクト フィルター オブジェクトを使用するため、イベントの要求ごとに新しいオブジェクトを返す必要があります。 イベントを起動するときに、イベント ハンドラーが呼び出されていることを確認するには、このフィルターを確認してください。  
  
 AutomationEvents.h と AutomationEvents.cpp には、宣言およびの次の表に、クラスの実装が含まれています。  
  
|クラス|説明|  
|-----------|-----------------|  
|`CAutomationEvents`|取得したイベントのルート オブジェクトを実装して、`DTE.Events`オブジェクト。|  
|`CProjectsEventsContainer` および `CProjectItemsEventsContainer`|対応するイベントを発生させるイベントのソース オブジェクトを実装します。|  
  
 次のコード例では、イベント オブジェクトに対する要求に応答する方法を示します。  
  
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
  
 上記のコードで`g_wszAutomationProjects`、プロジェクト コレクション ("FigProjects") の名前を指定`g_wszAutomationProjectsEvents`("FigProjectsEvents") と`g_wszAutomationProjectItemsEvents`("FigProjectItemEvents") は、プロジェクトのイベントの名前とプロジェクト項目のソースはイベント、VSPackage の実装です。  
  
 イベント オブジェクトを同じの一元化された場所から取得した、`DTE.Events`オブジェクト。 これにより、すべてのイベント オブジェクトはようにグループ化、エンドユーザーが特定のイベントを検索する全体のオブジェクト モデルを参照する必要はありません。 これはシステム全体のイベントのコードを実装する必要はなく、特定の VSPackage オブジェクトを提供することもできます。 ただし、エンドユーザーのユーザー見つける必要がありますのイベント、`ProjectItem`インターフェイス、明確ではないすぐにそのイベント オブジェクトが取得されるからです。  
  
## <a name="see-also"></a>参照  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>   
 [VSSDK のサンプル](http://aka.ms/vs2015sdksamples)