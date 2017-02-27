---
title: "Visual Studio SDK 内のイベントを公開します。 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "公開するイベント [Visual Studio]"
  - "オートメーション [Visual Studio SDK] イベントの公開"
ms.assetid: 70bbc258-c221-44f8-b0d7-94087d83b8fe
caps.latest.revision: 16
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 16
---
# Visual Studio SDK 内のイベントを公開します。
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] により、オートメーションを使用してソースのイベントを実行します。 プロジェクトとプロジェクト アイテムのイベントを取得するをお勧めします。  
  
 イベントがからオートメーションのコンシューマーによって取得された、 <xref:EnvDTE.DTEClass.Events%2A> オブジェクトまたは <xref:EnvDTE.DTEClass.GetObject%2A> ("EventObjectName") です。 環境の呼び出し `IDispatch::Invoke` を使用して、 `DISPATCH_METHOD` または `DISPATCH_PROPERTYGET` フラグをイベントを返します。  
  
 次のプロセスでは、VSPackage 固有のイベントを返す方法について説明します。  
  
1.  環境を起動します。  
  
2.  すべての VSPackages の自動化、AutomationEvents、AutomationProperties キーの下のすべての値名をレジストリから読み取るし、それらの名前をテーブルに格納します。  
  
3.  この例では、オートメーション コンシューマーを呼び出す `DTE.Events.AutomationProjectsEvents` または `DTE.Events.AutomationProjectItemsEvents`です。  
  
4.  環境では、テーブル内の文字列パラメーターを検索し、対応する VSPackage を読み込みます。  
  
5.  環境の呼び出し、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> 呼び出し AutomationProjectsEvents または AutomationProjectItemsEvents この例では、名前を使用してメソッドが渡されます。  
  
6.  VSPackage であり、メソッドなど、ルート オブジェクトを作成する `get_AutomationProjectsEvents` と `get_AutomationProjectItemEvents` し、オブジェクトに IDispatch ポインターを返します。  
  
7.  環境では、オートメーション呼び出しに渡された名に基づいて、適切なメソッドを呼び出します。  
  
8.   `get_` メソッドを実装する別の IDispatch ベースのイベント オブジェクトを作成、 `IConnectionPointContainer` インターフェイスおよび `IConnectionPoint` インターフェイスし、オブジェクトへの IDispatchpointer を返します。  
  
 イベントを公開するには、オートメーションを使用してに応答する必要があります <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> し、レジストリに追加する文字列。 基本的なプロジェクト サンプルでは、文字列は"BscProjectsEvents"と"BscProjectItemsEvents"です。  
  
## <a name="registry-entries-from-the-basic-project-sample"></a>基本的なプロジェクト サンプルからレジストリ エントリ  
 このセクションでは、オートメーション イベントの値をレジストリに追加する場所を示します。  
  
 [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0\Packages\\< PkgGUID\>\AutomationEvents]  
  
 「AutomationProjectEvents オブジェクトを返す AutomationProjectEvents「=」」  
  
 「AutomationProjectItemsEvents オブジェクトを返す AutomationProjectItemEvents「=」」  
  
|名前|型|範囲|説明|  
|----------|----------|-----------|-----------------|  
|既定値 (@)|REG_SZ|未使用|使用されていません。 ドキュメントには、データ フィールドを使用することができます。|  
|AutomationProjectsEvents|REG_SZ|イベント オブジェクトの名前。|キーの名前のみが関連します。 ドキュメントには、データ フィールドを使用することができます。<br /><br /> この例では、基本的なプロジェクト サンプルから取得されます。|  
|AutomationProjectItemEvents|REG_SZ|イベント オブジェクトの名前|キーの名前のみが関連します。 ドキュメントには、データ フィールドを使用することができます。<br /><br /> この例では、基本的なプロジェクト サンプルから取得されます。|  
  
 オートメーションのコンシューマーによって要求されると、イベント オブジェクトのいずれか、イベント、VSPackage をサポートするメソッドを持つルート オブジェクトを作成します。 環境を適切な呼び出します `get_` このオブジェクトのメソッドです。 たとえば場合、 `DTE.Events.AutomationProjectsEvents` が呼び出される、 `get_AutomationProjectsEvents` ルート オブジェクトのメソッドが呼び出されます。  
  
 ![Visual Studio プロジェクト イベント](../../extensibility/internals/media/projectevents.png "ProjectEvents")  
イベントのオートメーション モデル  
  
 クラス `CProjectEventsContainer` BscProjectsEvents のソース オブジェクトを表す、 `CProjectItemsEventsContainer` BscProjectItemsEvents のソース オブジェクトを表します。  
  
 ほとんどの場合は、ほとんどのイベント オブジェクトがフィルター オブジェクトをかかるためイベント要求ごとに新しいオブジェクトを返す必要があります。 イベントを発生させるイベント ハンドラーが呼び出されていることを確認するには、このフィルターを確認します。  
  
 AutomationEvents.h と AutomationEvents.cpp には、宣言およびの次の表に、クラスの実装が含まれています。  
  
|クラス|説明|  
|-----------|-----------------|  
|`CAutomationEvents`|取得したイベントのルート オブジェクトを実装して、 `DTE.Events` オブジェクトです。|  
|`CProjectsEventsContainer` および `CProjectItemsEventsContainer`|対応するイベントを発生させるイベントのソース オブジェクトを実装します。|  
  
 次のコード例では、イベント オブジェクトに対する要求に応答する方法を示します。  
  
```cpp#  
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
  
 、上記のコードで `g_wszAutomationProjects` 、プロジェクト コレクション ("FigProjects") の名前を指定 `g_wszAutomationProjectsEvents` ("FigProjectsEvents") と `g_wszAutomationProjectItemsEvents` ("FigProjectItemEvents")、プロジェクト イベントの名前とプロジェクト項目を VSPackage 実装からソースとするイベントです。  
  
 イベント オブジェクトが同一の中央の場所から取得した、 `DTE.Events` オブジェクトです。 これにより、すべてのイベント オブジェクトはようにグループ化、エンドユーザーが特定のイベントを検索する全体のオブジェクト モデルを参照する必要はありません。 システム全体のイベントのコードを実装する必要はなく、固有の VSPackage オブジェクトを提供するこのもできます。 ただし、エンド ユーザーのユーザー見つける必要がありますがイベントを `ProjectItem` インターフェイス、明確ではないすぐにそのイベント オブジェクトが取得されるからです。  
  
## <a name="see-also"></a>参照  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>   
 [VSSDK のサンプル](../../misc/vssdk-samples.md)