---
title: IManagedAddin::Load
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords: ''
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: b5f8e94ebcd0aec8e17cac8d651017ed1565d2ec
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/17/2018
---
# <a name="imanagedaddinload"></a>IManagedAddin::Load
  管理対象の VSTO アドインが読み込まれるときに呼び出されます。  
  
## <a name="syntax"></a>構文  
  
```c++
HRESULT Load([in] BSTR bstrManifestURL,   
             [in] IDispatch *pdispApplication);  
```  
  
### <a name="parameters"></a>パラメーター  
  
|パラメーター|説明|  
|---------------|-----------------|  
|*bstrManifestURL*|VSTO アドインのマニフェストの完全なパス。|  
|*pdispApplication*|VSTO アドインを読み込むホスト アプリケーションを表す IDispatch へのポインター。|  
  
## <a name="return-value"></a>戻り値  
 メソッドが正常に完了したかどうかを示す HRESULT 値。  
  
## <a name="remarks"></a>コメント  
 マニフェストは、VSTO アドインの読み込みに使用される情報を提供するファイル (通常は XML ファイル) です。 たとえば、マニフェストには、VSTO アドイン アセンブリの場所や、VSTO アドインが読み込まれるときにインスタンス化するエントリ ポイント クラスを指定できます。  
  
 *BstrManifestURL*パラメーターには値が含まれています、`Manifest`の下のエントリ、 **HKEY_CURRENT_USER\Software\Microsoft\Office\\_\<アプリケーション名>_ \Addins\\_\<アドイン ID >_**  VSTO アドインのレジストリ キー。 詳細については、次を参照してください。 [IManagedAddin インターフェイス](../vsto/imanagedaddin-interface.md)です。  
  
 読み込まれる VSTO アドインのアプリケーション ドメインやセキュリティ ポリシーの構成などのタスクを実行するように、 [IManagedAddIn::Load](../vsto/imanagedaddin-load.md) メソッドを実装します。  
  
## <a name="see-also"></a>関連項目  
 [IManagedAddin Interface](../vsto/imanagedaddin-interface.md)   
 [IManagedAddin::Unload](../vsto/imanagedaddin-unload.md)  
  
  