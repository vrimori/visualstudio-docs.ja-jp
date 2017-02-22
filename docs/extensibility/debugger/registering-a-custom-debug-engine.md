---
title: "カスタム デバッグ エンジンを登録します。 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "デバッグ エンジンは、登録します。"
ms.assetid: 9984cd3d-d34f-4662-9ace-31766499abf5
caps.latest.revision: 6
caps.handback.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
---
# カスタム デバッグ エンジンを登録します。
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

デバッグ エンジンは、必要があります上の COM 規則に従うクラス ファクトリとして登録だけでなく、Visual Studio のレジストリ サブキーを使用して Visual Studio で登録します。  
  
> [!NOTE]
>  一部として組み込まれた TextInterpreter サンプルには、デバッグ エンジンを登録する方法の例を参照して、 [Tutorial: Building a Debug Engine Using ATL COM](http://msdn.microsoft.com/ja-jp/9097b71e-1fe7-48f7-bc00-009e25940c24)です。  
  
## DLL のサーバー プロセス  
 通常、COM サーバーとして、独自の DLL のデバッグ エンジンを実装します。 これは、Visual Studio がアクセスする前に、デバッグ エンジンは、必要がありますを COM クラス ファクトリの CLSID を登録することを意味します。 デバッグ エンジンは、必要があります登録して自体 Visual Studio 自体で任意のプロパティ \(それ以外の場合のメトリックと呼ばれます\) を確立するためにデバッグ エンジンをサポートしています。 デバッグ エンジンは、Visual Studio のレジストリ サブキーに記述されているメトリックの選択は、デバッグ エンジンがサポートしている機能によって異なります。  
  
 [デバッグ用の SDK ヘルパー](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) だけでなく、レジストリの場所を記述、デバッグ エンジンを登録するために必要ですさまざまな便利な関数と簡単にレジストリを操作する、C\+\+ 開発者向けの宣言を含んでいる dbgmetric.lib ライブラリについても説明します。  
  
### 例  
 使用する方法を示す \(TextInterpreter サンプル\)」から一般的な例を次に、 `SetMetric` 関数 \(dbgmetric.lib\)、Visual Studio でデバッグ エンジンを登録します。 Dbgmetric.lib で渡されるメトリックも定義されます。  
  
> [!NOTE]
>  TextInterpreter は基本的なデバッグ エンジンです。実装していません\-は登録されませんし、その他の機能です。 詳細なデバッグ エンジンでの完全な一覧が必要があります `SetMetric` 呼び出しまたは同等の各機能のデバッグ エンジンのいずれかをサポートしています。  
  
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
  
## 参照  
 [カスタム デバッグ エンジンを作成します。](../../extensibility/debugger/creating-a-custom-debug-engine.md)   
 [デバッグ用の SDK ヘルパー](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)   
 [Tutorial: Building a Debug Engine Using ATL COM](http://msdn.microsoft.com/ja-jp/9097b71e-1fe7-48f7-bc00-009e25940c24)