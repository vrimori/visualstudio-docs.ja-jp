---
title: デバッグ エンジンのカスタムの登録 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, registering
ms.assetid: 9984cd3d-d34f-4662-9ace-31766499abf5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 7c87b3749c2ea63e89e2e8fb0caf773434a38df2
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2018
ms.locfileid: "44281391"
---
# <a name="register-a-custom-debug-engine"></a>カスタム デバッグ エンジンを登録します。
デバッグ エンジンする必要があります、次の COM 規則に従うクラス ファクトリとして登録だけでなく、Visual Studio のレジストリ サブキーから Visual Studio で登録します。  
  
> [!NOTE]
>  一部として組み込まれている TextInterpreter サンプルでは、デバッグ エンジンを登録する方法の例を見つけることができます、[チュートリアル: ATL COM を使用してデバッグ エンジンを構築する](https://msdn.microsoft.com/library/9097b71e-1fe7-48f7-bc00-009e25940c24)します。  
  
## <a name="dll-server-process"></a>サーバー プロセスの DLL  
 デバッグ エンジンは COM サーバーとしては、独自の DLL で通常設定します。 そのため、デバッグ エンジンする必要がありますクラス ファクトリの CLSID を COM 登録前に、Visual Studio でアクセスできます。 次に、デバッグ エンジンする必要がありますの登録に任意のプロパティ (それ以外の場合のメトリックと呼ばれます) を確立するために Visual Studio デバッグ エンジンをサポートしています。 Visual Studio のレジストリ サブキーに記述されたメトリックの選択は、デバッグ エンジンをサポートする機能によって異なります。  
  
 [デバッグ用の SDK ヘルパー](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)デバッグ エンジンでは; を登録するために必要なレジストリ位置だけでなくについても説明、 *dbgmetric.lib*ライブラリで、さまざまな便利な関数と宣言が含まれていますC++ 開発者にとって容易にレジストリを操作します。  
  
### <a name="example"></a>例  
 使用する方法を示します (TextInterpreter サンプル) から次の例、`SetMetric`関数 (から*dbgmetric.lib*)、Visual Studio を使用したデバッグ エンジンを登録します。 渡されるメトリックを定義も*dbgmetric.lib*します。  
  
> [!NOTE]
>  TextInterpreter は基本的なデバッグ エンジンです。設定しません-は登録されませんし、その他の機能です。 詳細なデバッグ エンジンでの完全な一覧が必要があります`SetMetric`呼び出しまたは同等のものでは、デバッグ エンジンの各機能の 1 つをサポートします。  
  
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
 [チュートリアル: ATL COM を使用してデバッグ エンジンを構築します。](https://msdn.microsoft.com/library/9097b71e-1fe7-48f7-bc00-009e25940c24)