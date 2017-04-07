---
title: "Visual Studio の展開時にプロダクト キーを自動的に適用する | Microsoft Docs"
ms.custom: 
ms.date: 3/10/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d79260be-6234-4fd3-89b5-a9756b4a93c1
caps.latest.revision: 10
author: TerryGLee
ms.author: tglee
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: 1d1e0c656b91049ce53456e6c5c011c08ca2e58e
ms.openlocfilehash: db051eaf8ef98928c0fec858e4cc9380a3b7687b
ms.lasthandoff: 03/11/2017

---
# <a name="automatically-apply-product-keys-when-deploying-visual-studio"></a>Visual Studio の展開時にプロダクト キーを自動的に適用する
Visual Studio の配置を自動化するために使用されるスクリプトの一部として、プログラム的にプロダクト キーを適用することができます。 プロダクト キーは、Visual Studio のインストール中またはインストール完了後に、プログラム的にデバイスで設定できます。  
  
## <a name="apply-the-license-during-installation"></a>インストール中にライセンスを適用する  
 Visual Studio のセットアップ プロセス中にプロダクト キーを適用するには、--productKey パラメーターを使用します。 既にエンドユーザーにライセンスが付与されている状態で Visual Studio をインストールする場合は、このセットアップ パラメーターを --quiet パラメーターとともに使用できます。 --productKey パラメーターを使用するには、コマンド プロンプトを開きます。 セットアップ プログラム (vs_enterprise.exe や vs_professional.exe など) を実行し、ダッシュが含まれている、または含まれていないプロダクト キー (25 文字) を指定して --productKey パラメーターを設定します。  
  
 以下に例として、プロダクト キー AAAAABBBBBCCCCCDDDDDEEEEEEE を指定して Visual Studio 2015 Enterprise をインストールする場合のコマンドを示します。  
  
 `vs_enterprise.exe [any other setup parameters] --productKey AAAAABBBBBCCCCCDDDDDDEEEEEE`  
  
## <a name="apply-the-license-after-installation"></a>インストール後にライセンスを適用する  
 ターゲット コンピューターにある storePID.exe ユーティリティをサイレント モードで使用して、インストールされているバージョンの Visual Studio をプロダクト キーでアクティブにすることができます。 StorePID.exe はユーティリティ プログラムで、Visual Studio で以下にインストールされます。**\<ドライブ>:\\\Program Files (x86)\Microsoft Visual Studio 15.0\Common7\IDE\StorePID.exe**  
  
 System Center エージェントまたは管理者特権でのコマンド プロンプトのいずれかを使用することにより、昇格された特権で storePID.exe を実行します。その際、プロダクト キー (ダッシュを含む) と Microsoft 製品コード (MPC) を後ろに付けます。 プロダクト キーには、絶対にダッシュ (-) を含めないください。  
  
 `StorePID.exe [product key including the dashes] [MPC]`  
  
 以下に例として、プロダクト キー「AAAAA-BBBBB-CCCCC-DDDDDD-EEEEEE」を指定して、MPC が 08860 の Visual Studio 2017 Enterprise をインストールする場合のコマンド ラインを示します。  
  
 `C:\Program Files (x86)\Microsoft Visual Studio 15.0\Common7\IDE\StorePID.exe AAAAA-BBBBB-CCCCC-DDDDDD-EEEEEE 08860`  
  
 次の表に、Visual Studio の各エディションの MPC コードを一覧します。  
  
|Visual Studio エディション|MPC|  
|---------------------------|---------|
|Visual Studio Enterprise 2017|08860|  
|Visual Studio Professional 2017|08862|  
|Visual Studio Test Professional 2017|08866| 
|Visual Studio Enterprise 2015|07060|  
|Visual Studio Professional 2015|07062|  
|Visual Studio Test Professional 2015|07066|  
|Visual Studio Ultimate 2013|06181|  
|Visual Studio Premium 2013|06191|  
|Visual Studio Professional 2013|06177|  
|Visual Studio Test Professional 2013|06194|  
  
StorePID.exe が正常にプロダクト キーを適用した場合は 0 を返します。 エラーが検出された場合は、1 ～ 6 の範囲の数値を返します。  
  
## <a name="see-also"></a>関連項目  
 [Visual Studio をインストールする](../install/install-visual-studio.md)
 [Visual Studio のオフライン インストールを作成する](../install/create-an-offline-installation-of-visual-studio.md)
