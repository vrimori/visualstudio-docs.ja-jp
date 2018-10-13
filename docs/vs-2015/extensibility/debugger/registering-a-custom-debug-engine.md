---
title: デバッグ エンジンのカスタムの登録 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debug engines, registering
ms.assetid: 9984cd3d-d34f-4662-9ace-31766499abf5
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 336320efce371d555854784e5fbbc60174340e03
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49303499"
---
# <a name="registering-a-custom-debug-engine"></a>カスタム デバッグ エンジンの登録
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

デバッグ エンジンする必要があります COM 規則に従うクラス ファクトリとして登録だけでなく、Visual Studio のレジストリ サブキーから Visual Studio で登録します。  
  
> [!NOTE]
>  一部として組み込まれている TextInterpreter サンプルでは、デバッグ エンジンを登録する方法の例があります、[チュートリアル: ビルド、デバッグ エンジンを使用して ATL COM](http://msdn.microsoft.com/en-us/9097b71e-1fe7-48f7-bc00-009e25940c24)します。  
  
## <a name="dll-server-process"></a>DLL のサーバー プロセス  
 通常、デバッグ エンジンは、COM サーバーとして、独自の DLL に実装されます。 つまり Visual Studio がアクセスする前に、デバッグ エンジンする必要がありますを COM クラス ファクトリの CLSID を登録します。 デバッグ エンジンする必要がありますの登録に Visual Studio 自体のプロパティ (それ以外の場合のメトリックと呼ばれます) を確立するには、デバッグし、エンジンをサポートしています。 デバッグ エンジンの Visual Studio のレジストリ サブキーに書き込まれるメトリックの選択は、デバッグ エンジンをサポートする機能によって異なります。  
  
 [デバッグ用の SDK ヘルパー](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)だけでなく、レジストリの場所を記述デバッグ エンジンでは; を登録するために必要なさまざまな便利な関数と、C++ 開発者向けの宣言を含む dbgmetric.lib ライブラリもについて説明します。簡単にレジストリを操作します。  
  
### <a name="example"></a>例  
 使用する方法を示す (TextInterpreter サンプル) から一般的な例を次に、`SetMetric`関数 (dbgmetric.lib)、Visual Studio を使用したデバッグ エンジンを登録します。 渡されるメトリックは、dbgmetric.lib でも定義されます。  
  
> [!NOTE]
>  TextInterpreter は基本的なデバッグ エンジンです。実装していない-は登録されませんし、その他の機能です。 詳細なデバッグ エンジンでの完全な一覧が必要があります`SetMetric`呼び出しまたは同等のものでは、デバッグ エンジンの各機能の 1 つをサポートします。  
  
```  
// Define base registry subkey to Visual Studio.  
static const WCHAR strRegistrationRoot[] = L"Software\\Microsoft\\VisualStudio\\8.0";  
  
HRESULT CTextInterpreterModule::RegisterServer(BOOL bRegTypeLib, const CLSID * pCLSID)  
{  
    SetMetric(metrictypeEngine, __uuidof(Engine), metricName, L"Text File", false, strRegistrationRoot);  
    SetMetric(metrictypeEngine, __uuidof(Engine), metricCLSID, CLSID_Engine, false, strRegistrationRoot);  
    SetMetric(metrictypeEngine, __uuidof(Engine), metricProgramProvider, CLSID_MsProgramProvider, false, strRegistrationRoot);  
  
    return base::RegisterServer(bRegTypeLib, pCLSID);  
}  
```  
  
## <a name="see-also"></a>関連項目  
 [カスタム デバッグ エンジンを作成します。](../../extensibility/debugger/creating-a-custom-debug-engine.md)   
 [デバッグ用の SDK ヘルパー](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)   
 [チュートリアル: ATL COM を使用してデバッグ エンジンを構築します。](http://msdn.microsoft.com/en-us/9097b71e-1fe7-48f7-bc00-009e25940c24)

