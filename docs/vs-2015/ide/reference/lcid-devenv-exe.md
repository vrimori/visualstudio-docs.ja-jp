---
title: -LCID (devenv.exe) | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- language default
- locale IDs, setting for IDE
- Devenv, /LCID switch
- locale IDs
- /l Devenv switch
- LCID devenv switch
- /lcid Devenv switch
ms.assetid: 3a3f4e70-ea66-4351-9d62-acb1dec30e8e
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 242e0055e59312cba616859e08a2a61a45064e66
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49301913"
---
# <a name="lcid-devenvexe"></a>/LCID (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
統合開発環境 (IDE) 内の文字列、通貨、およびその他の値に使用する既定の言語を設定します。  
  
## <a name="syntax"></a>構文  
  
```  
devenv {/LCID|/l} LocaleID  
```  
  
## <a name="arguments"></a>引数  
 `LocaleID`  
 必須。 指定する言語の LCID (ロケール ID)。  
  
## <a name="remarks"></a>Remarks  
 IDE を読み込み、環境用の既定の自然言語を設定します。 この変更はセッション間で保持され、IDE の **[オプション]** ダイアログ ボックスにある **[環境]** オプションの **[国際対応の設定]** ウィンドウに反映されます。  
  
 指定した言語がユーザーのシステムで使用できない場合、/LCID スイッチは無視されます。  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] でサポートされる言語の LCID の一覧を次の表に示します。  
  
|言語|LCID|  
|--------------|----------|  
|中国語 (簡体字、中国)|2052|  
|では |1028|  
|英語|1033|  
|フランス語|1036|  
|ドイツ語|1031|  
|イタリア語|1040|  
|日本語|1041|  
|韓国語|1042|  
|スペイン語|3082|  
  
## <a name="example"></a>例  
 この例では、英語のリソース文字列を使用して IDE を読み込みます。  
  
```  
devenv /LCID 1033  
```  
  
## <a name="see-also"></a>関連項目  
 [Devenv コマンド ライン スイッチ](../../ide/reference/devenv-command-line-switches.md)   
 [[国際対応の設定] \([オプション] ダイアログ ボックス - [環境])](../../ide/reference/international-settings-environment-options-dialog-box.md)   
 [ウィンドウ レイアウトをカスタマイズする](../../ide/customizing-window-layouts-in-visual-studio.md)



