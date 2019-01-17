---
title: '方法: ビジュアライザーをインストール |Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugger, visualizers
- visualizers, installing
ms.assetid: 3310ef43-515c-4d97-b0f9-51047247d3da
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e62637581fbb65eb8efd20e048cc364895cfbcdc
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53914572"
---
# <a name="how-to-install-a-visualizer"></a>方法: ビジュアライザーをインストールする
作成したビジュアライザーは、インストールして初めて [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] で使用できるようになります。 ビジュアライザーのインストールは簡単です。  
  
> [!NOTE]
>  UWP アプリでは、標準のテキストだけでは、HTML、XML、および JSON ビジュアライザーがサポートされます。 カスタム (ユーザーが作成した) ビジュアライザーはサポートされていません。  
  
### <a name="to-install-a-visualizer"></a>ビジュアライザーをインストールするには  
  
1.  作成したビジュアライザーを含むダイナミック リンク ライブラリ (DLL: Dynamic Link Library) を探します。  
  
2.  DLL を次のいずれかの場所にコピーします。  
  
    -   *VisualStudioInstallPath* `\Common7\Packages\Debugger\Visualizers`  
  
    -   `My Documents\` *VisualStudioVersion* `\Visualizers`  
  
3.  マネージド ビジュアライザーをリモート デバッグで使用するには、DLL をリモート コンピューター上の同じパスにコピーします。  
  
4.  デバッグ セッションを再開します。  
  
## <a name="see-also"></a>「  
 [カスタム ビジュアライザーを作成する](../debugger/create-custom-visualizers-of-data.md)   
 [方法: ビジュアライザーを記述する](/visualstudio/debugger/create-custom-visualizers-of-data)