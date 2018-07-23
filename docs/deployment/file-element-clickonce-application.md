---
title: '&lt;ファイル&gt;要素 (ClickOnce アプリケーション) |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: reference
f1_keywords:
- http://www.w3.org/2000/09/xmldsig#Transform
- urn:schemas-microsoft-com:asm.v2#file
- http://www.w3.org/2000/09/xmldsig#DigestValue
- http://www.w3.org/2000/09/xmldsig#DigestMethod
- http://www.w3.org/2000/09/xmldsig#Transforms
- urn:schemas-microsoft-com:asm.v2#hash
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <file> element [ClickOnce application manifest]
- manifests [ClickOnce], file element
ms.assetid: 56e3490c-eed5-4841-b1bf-eefe778b6ac9
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a487ac60ff789457f386754262b9d8fe1ceef9c4
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/17/2018
ms.locfileid: "39080596"
---
# <a name="ltfilegt-element-clickonce-application"></a>&lt;ファイル&gt;要素 (ClickOnce アプリケーション)
アセンブリ以外のファイルをすべてダウンロードして、アプリケーションで使用されるを識別します。  
  
## <a name="syntax"></a>構文  
  
```xml  
<file  
    name  
    size  
    group  
    optional  
    writeableType  
>  
    <typelib  
        tlbid  
        version  
        helpdir  
        resourceid  
        flags  
    />  
    <comClass  
        clsid  
        description  
        threadingModel  
        tlbid  
        progid  
        miscStatus  
        miscStatusIcon  
        miscStatusContent  
        miscStatusDocPrint  
        miscStatusThumbnail  
    />  
    <comInterfaceExternalProxyStub  
        iid  
        baseInterface  
        numMethods  
        name  
        tlbid  
        proxyStubClass32  
    />  
    <comInterfaceProxyStub  
        iid  
        baseInterface  
        numMethods  
        name  
        tlbid  
        proxyStubClass32  
    />  
    <windowClass  
        versioned  
    />  
</file>  
```  
  
## <a name="elements-and-attributes"></a>要素と属性  
 `file` 要素は省略可能です。 要素には、次の属性があります。  
  
|属性|説明|  
|---------------|-----------------|  
|`name`|必須。 ファイルの名前を識別します。|  
|`size`|必須。 ファイルのバイト単位のサイズを指定します。|  
|`group`|場合は、オプション、`optional`属性が指定されていないかに設定`false`; 場合は必須`optional`は`true`します。 このファイルが所属するグループの名前。 名前は、開発者が選択した任意の Unicode 文字列値を指定でき、オンデマンドでのファイルをダウンロードするために使用、<xref:System.Deployment.Application.ApplicationDeployment>クラス。|  
|`optional`|任意。 このファイルにする必要があるかどうか、アプリケーションが最初にダウンロードを実行、またはオンデマンドで、アプリケーションが要求されるまで、サーバーにのみに存在する必要がありますファイルのかどうかを指定します。 場合`false`または未定義の場合に、アプリケーションが初めて実行したり、インストールされているときに、ファイルはダウンロードされます。 場合`true`、`group`を有効にするアプリケーション マニフェストを指定する必要があります。 `optional` true にできない場合`writeableType`値を指定した`applicationData`します。|  
|`writeableType`|任意。 このファイルがデータ ファイルであることを指定します。 現在、唯一の有効な値は`applicationData`します。|  
  
## <a name="typelib"></a>タイプ ライブラリ  
 `typelib`要素は、ファイルの要素のオプションの子。 要素には、COM コンポーネントが属しているタイプ ライブラリがについて説明します。 要素には、次の属性があります。  
  
|属性|説明|  
|---------------|-----------------|  
|`tlbid`|必須。 タイプ ライブラリに割り当てられた GUID です。|  
|`version`|必須。 タイプ ライブラリのバージョン番号。|  
|`helpdir`|必須。 コンポーネントのヘルプ ファイルを格納するディレクトリ。 長さ 0 の場合があります。|  
|`resourceid`|任意。 ロケール識別子 (LCID) の 16 進数文字列形式。 1 ~ 4 個 16 進数 0 x プレフィックスなし、先行ゼロなしになります。 ニュートラル副言語識別子を LCID があります。|  
|`flags`|任意。 このタイプ ライブラリのタイプ ライブラリ フラグの文字列形式。 具体的には、"RESTRICTED"、"CONTROL"、"HIDDEN"および"HASDISKIMAGE"のいずれかが必要です。|  
  
## <a name="comclass"></a>comClass  
 `comClass`要素のオプションの子では、`file`要素が必要な場合、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]アプリケーションには、登録を必要としない COM を使用してデプロイする予定の COM コンポーネントが含まれています。 要素には、次の属性があります。  
  
|属性|説明|  
|---------------|-----------------|  
|`clsid`|必須。 GUID で表される COM コンポーネントのクラス ID。|  
|`description`|任意。 クラス名。|  
|`threadingModel`|任意。 インプロセス COM クラスで使用されるスレッド処理モデル。 このプロパティが null の場合、スレッド処理モデルは使用されません。 コンポーネントがクライアントのメイン スレッドで作成され、他のスレッドからの呼び出しは、このスレッドにマーシャ リングされます。 次に、有効な値を示します。<br /><br /> `Apartment`、`Free`、`Both`、および `Neutral`。|  
|`tlbid`|任意。 この COM コンポーネントのタイプ ライブラリの GUID です。|  
|`progid`|任意。 バージョンに依存する COM コンポーネントに関連付けられたプログラム id。 形式を`ProgID`は`<vendor>.<component>.<version>`します。|  
|`miscStatus`|任意。 アセンブリ内の重複によって提供される情報をマニフェスト、`MiscStatus`レジストリ キー。 場合の値を`miscStatusIcon`、 `miscStatusContent`、 `miscStatusDocprint`、または`miscStatusThumbnail`属性が見つからない場合は、対応する既定値が記載`miscStatus`して足りない属性を使用します。 値は、次の表の属性値のコンマ区切りの一覧を指定できます。 COM クラスが必要とする OCX クラスである場合は、この属性を使用することができます`MiscStatus`レジストリ キーの値。|  
|`miscStatusIcon`|任意。 アセンブリ内の重複はマニフェスト DVASPECT_ICON によって提供される情報です。 オブジェクトのアイコンを提供できます。 値は、次の表の属性値のコンマ区切りの一覧を指定できます。 COM クラスが必要とする OCX クラスである場合は、この属性を使用することができます`Miscstatus`レジストリ キーの値。|  
|`miscStatusContent`|任意。 アセンブリ内の重複はマニフェスト DVASPECT_CONTENT によって提供される情報です。 画面またはプリンターの表示可能な複合ドキュメントを提供できます。 値は、次の表の属性値のコンマ区切りの一覧を指定できます。 COM クラスが必要とする OCX クラスである場合は、この属性を使用することができます`MiscStatus`レジストリ キーの値。|  
|`miscStatusDocPrint`|任意。 アセンブリ内の重複はマニフェスト DVASPECT_DOCPRINT によって提供される情報です。 プリンターに印刷される場合、画面に表示可能なオブジェクト表現を提供できます。 値は、次の表の属性値のコンマ区切りの一覧を指定できます。 COM クラスが必要とする OCX クラスである場合は、この属性を使用することができます`MiscStatus`レジストリ キーの値。|  
|`miscStatusThumbnail`|任意。 アセンブリ内の重複はマニフェスト DVASPECT_THUMBNAIL によって提供される情報です。 参照ツールで表示可能なオブジェクトのサムネイルを提供できます。 値は、次の表の属性値のコンマ区切りの一覧を指定できます。 COM クラスが必要とする OCX クラスである場合は、この属性を使用することができます`MiscStatus`レジストリ キーの値。|  
  
## <a name="cominterfaceexternalproxystub"></a>comInterfaceExternalProxyStub  
 `comInterfaceExternalProxyStub`要素のオプションの子では、`file`要素が場合に必要な可能性があります、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]アプリケーションには、登録を必要としない COM を使用してデプロイする予定の COM コンポーネントが含まれています。 要素には、次の属性が含まれています。  
  
|属性|説明|  
|---------------|-----------------|  
|`iid`|必須。 インターフェイス ID (IID) はこのプロキシによって処理されます。 IID は、中かっこで囲む必要があります。|  
|`baseInterface`|任意。 インターフェイスが参照元のインターフェイスの IID`iid`が派生します。|  
|`numMethods`|任意。 インターフェイスによって実装されるメソッドの数。|  
|`name`|任意。 インターフェイスの名前は、コードに表示されます。|  
|`tlbid`|任意。 指定されたインターフェイスの説明を格納するタイプ ライブラリ、`iid`属性。|  
|`proxyStubClass32`|任意。 32 ビット プロキシ Dll の CLSID を IID にマップします。|  
  
## <a name="cominterfaceproxystub"></a>comInterfaceProxyStub  
 `comInterfaceProxyStub`要素のオプションの子では、`file`要素が場合に必要な可能性があります、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]アプリケーションには、登録を必要としない COM を使用してデプロイする予定の COM コンポーネントが含まれています。 要素には、次の属性が含まれています。  
  
|属性|説明|  
|---------------|-----------------|  
|`iid`|必須。 インターフェイス ID (IID) はこのプロキシによって処理されます。 IID は、中かっこで囲む必要があります。|  
|`baseInterface`|任意。 インターフェイスが参照元のインターフェイスの IID`iid`が派生します。|  
|`numMethods`|任意。 インターフェイスによって実装されるメソッドの数。|  
|`Name`|任意。 インターフェイスの名前は、コードに表示されます。|  
|`Tlbid`|任意。 指定されたインターフェイスの説明を格納するタイプ ライブラリ、`iid`属性。|  
|`proxyStubClass32`|任意。 32 ビット プロキシ Dll の CLSID を IID にマップします。|  
|`threadingModel`|任意。 任意。 インプロセス COM クラスで使用されるスレッド処理モデル。 このプロパティが null の場合、スレッド処理モデルは使用されません。 コンポーネントがクライアントのメイン スレッドで作成され、他のスレッドからの呼び出しは、このスレッドにマーシャ リングされます。 次に、有効な値を示します。<br /><br /> `Apartment`、`Free`、`Both`、および `Neutral`。|  
  
## <a name="windowclass"></a>windowClass  
 `windowClass`要素のオプションの子では、`file`要素が場合に必要な可能性があります、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]アプリケーションには、登録を必要としない COM を使用してデプロイする予定の COM コンポーネントが含まれています。 要素は、対象となるバージョンが必要な COM コンポーネントによって定義ウィンドウ クラスを参照します。 要素には、次の属性が含まれています。  
  
|属性|説明|  
|---------------|-----------------|  
|`versioned`|任意。 ウィンドウ クラスを含むアセンブリのバージョンを含む内部ウィンドウ クラスの登録で使用される名前かどうかを制御します。 この属性の値を指定できます`yes`または`no`します。 既定値は `yes` です。 値`no`同じウィンドウ クラスは、サイド バイ サイド コンポーネントと同等の非-並列でのコンポーネントによって定義され、同じウィンドウ クラスとして扱われるようにする場合にのみ使用する必要があります。 ウィンドウ クラスの登録に関する通常の規則が適用されます — だけが適用されて、バージョンがあるないため、ウィンドウ クラスを登録する最初のコンポーネントは、登録することができます。|  
  
## <a name="hash"></a>hash  
 `hash`要素のオプションの子では、`file`要素。 `hash`要素に属性がありません。  
  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] デプロイ後に変更されたファイルがないことを確認するのに、セキュリティ チェックとして、アプリケーションでのすべてのファイルのアルゴリズム、ハッシュを使用します。 場合、`hash`要素が含まれていない、このチェックは実行されません。 そのため、省略すると、`hash`要素はお勧めしません。  
  
 そのマニフェストがデジタル署名することはできない場合は、マニフェストには、ハッシュされていないファイルが含まれています、署名済み、ユーザーは、ハッシュされていないファイルの内容を確認できないためです。  
  
## <a name="dsigtransforms"></a>dsig:Transforms  
 `dsig:Transforms`要素の必須の子では、`hash`要素。 `dsig:Transforms`要素に属性がありません。  
  
## <a name="dsigtransform"></a>dsig:Transform  
 `dsig:Transform`要素の必須の子では、`dsig:Transforms`要素。 `dsig:Transform`要素には、次の属性。  
  
|属性|説明|  
|---------------|-----------------|  
|`Algorithm`|このファイルのダイジェストを計算するために使用するアルゴリズム。 現在、唯一の値で使用される[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]は`urn:schemas-microsoft-com:HashTransforms.Identity`します。|  
  
## <a name="dsigdigestmethod"></a>dsig:DigestMethod  
 `dsig:DigestMethod`要素の必須の子では、`hash`要素。 `dsig:DigestMethod`要素には、次の属性。  
  
|属性|説明|  
|---------------|-----------------|  
|`Algorithm`|このファイルのダイジェストを計算するために使用するアルゴリズム。 現在、唯一の値で使用される[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]は`http://www.w3.org/2000/09/xmldsig#sha1`します。|  
  
## <a name="dsigdigestvalue"></a>目的  
 `dsig:DigestValue`要素の必須の子では、`hash`要素。 `dsig:DigestValue`要素に属性がありません。 テキスト値は、指定したファイルの計算されたハッシュです。  
  
## <a name="remarks"></a>Remarks  
 この要素が、アプリケーションを構成するすべてのアセンブリ以外のファイルを識別し、具体的には、検証のファイルのハッシュ値。 この要素は、ファイルに関連付けられているコンポーネント オブジェクト モデル (COM) 分離データを含めることもできます。 ファイルが変更された場合、アプリケーション マニフェスト ファイルも変更を反映するように更新する必要があります。  
  
## <a name="example"></a>例  
 次のコード例を示しています`file`アプリケーション内の要素を使用してデプロイされたアプリケーションのマニフェストの[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]します。  
  
```xml  
<file name="Icon.ico" size="9216">  
  <hash>  
    <dsig:Transforms>  
      <dsig:Transform Algorithm="urn:schemas-microsoft-com:HashTransforms.Identity" />  
    </dsig:Transforms>  
    <dsig:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />  
    <dsig:DigestValue>lVoj+Rh6RQ/HPNLOdayQah5McrI=</dsig:DigestValue>  
  </hash>  
</file>  
```  
  
## <a name="see-also"></a>関連項目  
 [ClickOnce アプリケーション マニフェスト](../deployment/clickonce-application-manifest.md)