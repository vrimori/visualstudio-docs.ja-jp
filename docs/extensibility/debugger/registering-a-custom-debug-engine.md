---
title: "デバッグ エンジンが、カスタムの登録 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: debug engines, registering
ms.assetid: 9984cd3d-d34f-4662-9ace-31766499abf5
caps.latest.revision: "6"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 50903d9b45828725da03c0fcb0db0f08d7f884eb
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="registering-a-custom-debug-engine"></a>カスタム デバッグ エンジンを登録します。
デバッグ エンジン必要があります COM 規則に従うクラス ファクトリとして登録だけでなく、Visual Studio のレジストリ サブキーを Visual Studio に登録します。  
  
> [!NOTE]
>  デバッグ エンジンを登録する方法の例は含まれて、TextInterpreter サンプルについては、一部として構築された、[チュートリアル: ビルド、デバッグ エンジンを使用して ATL COM](http://msdn.microsoft.com/en-us/9097b71e-1fe7-48f7-bc00-009e25940c24)です。  
  
## <a name="dll-server-process"></a>DLL のサーバー プロセス  
 通常、COM サーバーとして、独自の DLL のデバッグ エンジンを実装します。 これは、Visual Studio がアクセスする前に、デバッグ エンジン必要がありますを COM クラス ファクトリの CLSID を登録することを意味します。 デバッグ エンジン必要があります登録して自体 Visual Studio 自体で任意のプロパティ (それ以外の場合のメトリックと呼ばれます) を確立するために、デバッグ エンジンをサポートしています。 デバッグ エンジンの Visual Studio のレジストリ サブキーに書き込まれるメトリックの選択は、デバッグ エンジンをサポートしている機能によって異なります。  
  
 [デバッグ用の SDK ヘルパー](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)だけでなく、レジストリの場所を記述するデバッグ エンジンを登録するために必要な多数の便利な関数と、C++ 開発者向けの宣言を含んでいる dbgmetric.lib ライブラリもについて説明します。簡単にレジストリを操作します。  
  
### <a name="example"></a>例  
 使用する方法を示す (TextInterpreter サンプル) から、一般的な例を次に示します、`SetMetric`関数 (dbgmetric.lib)、Visual Studio でデバッグ エンジンを登録します。 渡されるメトリックは、dbgmetric.lib も定義されています。  
  
> [!NOTE]
>  TextInterpreter は基本的なデバッグ エンジンです。実装していない — は登録されませんし、その他の機能です。 詳細なデバッグ エンジンでの完全な一覧が必要があります`SetMetric`呼び出しまたは同等の各機能のデバッグ エンジンのいずれかをサポートしています。  
  
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
  
## <a name="see-also"></a>参照  
 [カスタム デバッグ エンジンを作成します。](../../extensibility/debugger/creating-a-custom-debug-engine.md)   
 [デバッグ用の SDK ヘルパー](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)   
 [チュートリアル: ATL COM を使用してデバッグ エンジンを構築します。](http://msdn.microsoft.com/en-us/9097b71e-1fe7-48f7-bc00-009e25940c24)