---
title: 'クライアント管理の Macs の構成項目を作成する '
titleSuffix: Configuration Manager
description: Configuration Manager の Mac OS X 構成項目使用して、Mac OS X デバイスの設定を管理します。
ms.date: 05/08/2019
ms.prod: configuration-manager
ms.technology: configmgr-compliance
ms.topic: conceptual
ms.assetid: 722d5bf5-bedc-4dfc-b324-6eeb773874e9
author: aczechowski
manager: dougeby
ms.author: aaroncz
ms.openlocfilehash: 219ddd4c828cdabd022deb9fe372718184a4c024
ms.sourcegitcommit: bbf820c35414bf2cba356f30fe047c1a34c5384d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/21/2020
ms.locfileid: "81693430"
---
# <a name="create-configuration-items-for-mac-os-x-devices"></a>Mac OS X デバイスの構成項目を作成する
Configuration Manager の **[Mac OS X (カスタム)]** 構成アイテムを使用して、構成マネージャー クライアントで管理されている Mac OS X デバイスの設定を管理します。  
  
Mac OS X オペレーティング システムでは、アプリケーション設定を保存するためにプロパティ リスト (.plist) ファイルが使用されます。 コンプライアンス設定を使用して、プロパティの一覧ファイルの設定を評価および修復します。 また、コンプライアンスについて評価および修復できる値を返すシェル スクリプトを記述することで、Mac OS X の設定を管理することもできます。  
  
## <a name="create-a-custom-mac-os-x-configuration-item"></a>カスタム Mac OS X 構成アイテムを作成する  
  
1. Configuration Manager コンソールで、 **[資産とコンプライアンス]** を選択します。  
  
2. **[資産とコンプライアンス]** ワークスペースで **[コンプライアンス設定]** を展開してから、 **[構成アイテム]** を選択します。  
  
3. **[ホーム]** タブの **[作成]** グループで、 **[構成アイテムの作成]** を選択します。  
  
4. **[構成アイテムの作成]** ウィザードの **[全般]** ページで、構成アイテムの名前と、必要に応じて説明を入力します。  
  
5. **[作成する構成項目の種類の指定]** で、 **[Mac OS X (カスタム)]** を選択します。  
  
6. Configuration Manager コンソールで構成アイテムを検索およびフィルター処理するためにカテゴリを作成して割り当てる場合、 **[カテゴリ]** を選択します。  
  
7. ウィザードの **[サポートされているプラットフォーム]** ページで、構成項目を評価する特定の Mac OS X バージョンを選択します。  
  
8. ウィザードの **[設定]** ページで、Mac コンピューターでのコンプライアンスのために評価される新しい設定を追加します。 **[新規作成]** を選択して、 **[設定の作成]** ダイアログ ボックスを開きます。  
  
9. **[設定の作成]** ダイアログ ボックスで、設定の一意の名前と説明を入力します。  
  
10. 目的の **[設定の種類]** を選択し、必要な情報を指定します。  
  
    -   **Mac OS X の設定**  
  
        -   **アプリケーション ID**:コンプライアンスのキーを評価する、プロパティ リスト ファイルのアプリケーション ID を指定します。  
  
             たとえば、Safari Web ブラウザーの設定を編集する場合は、ことができます **com.apple.Safari.plist**です。  
  
        -   **キー**:Mac コンピューターでのコンプライアンスを評価するキーの名前を指定します。 */<ディクショナリ\>/<キー名\>* という構文を使用します。  
  
            > [!IMPORTANT]  
            >  キー名では大文字と小文字が区別され、それが Mac コンピューターのキー名と異なる場合は評価されません。 また、指定したキー名は後から編集できません。 キー名を編集する必要がある場合は、設定を削除してから再作成してください。  
  
    -   **スクリプト**  
  
        -   **探索スクリプト**: **[スクリプトの追加]** を選択した後、Mac コンピューターで設定のコンプライアンスを評価するシェル スクリプトを入力します。 シェル スクリプトで **echo** コマンドを使用し、コンプライアンスを評価するために Configuration Manager に値を返します。 Configuration Manager は、**STDOUT** で返された結果を使用して、コンプライアンスを評価します。  
  
            > [!IMPORTANT]  
            >  探索スクリプトに **reboot** コマンドは含めないでください。 探索スクリプトはクライアントが再起動するたびに実行されるため、これによって Mac コンピューターが連続して再起動されます。  
  
        -   **修復スクリプト (オプション)** :必要に応じて、 **[スクリプトの追加]** を選択してから、Mac クライアント コンピューターで見つかった非対応の設定を修復するときに使用するシェル スクリプトを入力します。  
  
            > [!IMPORTANT]  
            >  Mac コンピューターが解釈できない文字の書式設定が適用されないようにするために、コピーと貼り付けは使用しないでください。 代わりに、スクリプトの文字を直接入力してください。  
  
11. 設定の評価に使用する前に、条件の戻り値となるデータの形式である **[データ型]** を選択します。  
  
    > [!NOTE]  
    >  **[浮動小数点]** データの種類は、小数点第 3 位までをサポートしています。  
    >   
    >  Configuration Manager では、Mac 構成アイテムのスクリプト設定用に**ブール値**データ型の使用がサポートされていません。 代わりに、データ型を**整数**に設定し、スクリプトにより必ず整数値が返されるようにします。  
  
12. **[OK]** を選択して設定を保存し、 **[設定の作成]** ダイアログ ボックスを閉じます。 次に、引き続き必要な数だけ設定を追加します。  
  
13. ウィザードの **[コンプライアンス規則]** ページで、構成アイテムのコンプライアンスを定義する条件を指定します。 設定のコンプライアンスを評価するには、コンプライアンス規則が少なくとも 1 つ必要です。 **[新規作成]** を選択して、新しい規則を追加します。  
  
14. **[規則の作成]** ダイアログ ボックスで、次の情報を入力します。  
  
    -   **名前**:コンプライアンス規則の名前を入力します。  
  
    -   **説明**:コンプライアンス規則の説明を入力します。  
  
    -   **[選択した設定]:** **[参照]** を選択し、 **[設定の選択]** ダイアログ ボックスを開きます。 規則を定義する設定を選択するか、または **[新しい設定]** を選択します。 完了したら、 **[選択]** を選択します。  
  
        > [!TIP]  
        >  また、 **[プロパティ]** を選択して、現在選択されている設定についての情報を表示させることもできます。  
  
    -   **ルールの種類**: 使用するコンプライアンス規則の種類を選択します。  
  
        -   **値**:指定する値と構成項目によって返される値を比較するルールを作成します。  
  
        -   **存在**:デバイス上に存在するかどうかに応じて、設定を評価する規則を作成します。  
  
    -   **[値]** の種類の規則では、次の情報を指定します:  
  
        -   **設定は、次の規則に従う必要があります**:演算子と、選択した設定とのコンプライアンスのために評価される値を選択します。 使用できる演算子は次のとおりです。  
  
            -   **次の値と等しい**  
  
            -   **次の値に等しくない**  
  
            -   **次の値より大きい**  
  
            -   **次の値より小さい**  
  
            -   **次の値の間**  
  
            -   **次の値以上**  
  
            -   **次の値以下**  
  
            -   **次のいずれか**:テキストボックスで 1 行ごとに 1 つのエントリを指定します。  
  
            -   **次のいずれでもない**:テキストボックスで 1 行ごとに 1 つのエントリを指定します。  
  
        -   **サポートされている場合は準拠していない規則を修復する**:このオプションを選択すると、Configuration Manager によってコンプライアンス非対応の規則が自動的に修復されます。  
  
            > [!IMPORTANT]  
            >  コンプライアンス非対応の規則は、演算子が **[等しい]** に設定されている場合にのみ修復されます。  
  
        -   **この設定インスタンスが見つからない場合はコンプライアンス非対応としてレポートする**:この設定が Mac コンピューター上に見つからなかった場合、構成アイテムによりコンプライアンス非対応が報告されます。  
  
        -   **レポートするコンプライアンス非対応の重要度**:このコンプライアンス規則が満たされていなかった場合に報告される重要度レベルを指定します。 重要度レベルは次のとおりです。  
  
            -   **なし**: このコンプライアンス規則を満たしていないコンピューターでは、Configuration Manager レポート用に非対応重要度が何も報告されません。  
  
            -   **情報**: このコンプライアンス規則を満たしていないコンピューターは、Configuration Manager レポート用に**情報**というレベルでエラーの重要度を報告します。  
  
            -   **警告**: このコンプライアンス規則を満たしていないコンピューターは、Configuration Manager レポート用に**警告**というレベルでエラーの重要度を報告します。  
  
            -   **重大**: このコンプライアンス規則を満たしていないコンピューターは、Configuration Manager レポート用に**重大**というレベルでエラーの重要度を報告します。  
  
            -   **重大 (イベント)** : このコンプライアンス規則を満たしていないコンピューターは、Configuration Manager レポート用に**重大**というレベルでエラーの重要度を報告します。 Mac クライアント コンピューターは、この重要度レベルもログに記録します。  
  
    -   **[存在]** の種類の規則では、次の情報を指定します:  
  
        -   次のいずれかを選択します。  
  
            -   **この設定はクライアント デバイスに存在しなければならない**  
  
            -   **この設定はクライアント デバイスに存在してはならない**  
  
        -   **レポートするコンプライアンス非対応の重要度**:このコンプライアンス規則が満たされていなかった場合に報告される重要度レベルを指定します。 重要度レベルは次のとおりです。  
  
            -   **なし**: このコンプライアンス規則を満たしていないコンピューターでは、Configuration Manager レポート用に非対応重要度が何も報告されません。  
  
            -   **情報**: このコンプライアンス規則を満たしていないコンピューターは、Configuration Manager レポート用に**情報**というレベルでエラーの重要度を報告します。  
  
            -   **警告**: このコンプライアンス規則を満たしていないコンピューターは、Configuration Manager レポート用に**警告**というレベルでエラーの重要度を報告します。  
  
            -   **重大**: このコンプライアンス規則を満たしていないコンピューターは、Configuration Manager レポート用に**重大**というレベルでエラーの重要度を報告します。  
  
            -   **重大 (イベント)** : このコンプライアンス規則を満たしていないコンピューターは、Configuration Manager レポート用に**重大**というレベルでエラーの重要度を報告します。 Mac クライアント コンピューターは、この重要度レベルもログに記録します。  
  
        > [!NOTE]  
        >  表示されるオプションは、規則を構成する設定の種類によって異なる場合があります。  
  
15. **[OK]** を選択して **[規則の作成]** ダイアログ ボックスを閉じます。  
  
16. **[概要]** ページで、新しい構成項目の設定を確認します。 その後、ウィザードを完了します。  
  
**[資産とコンプライアンス]** ワークスペースの **[構成アイテム]** ノードにある新しい構成アイテムを確認します。  
  
ここで、この構成項目を構成基準に追加する場合は、「[構成基準を作成する方法](../../compliance/deploy-use/create-configuration-baselines.md)」を参照してください。  
  
## <a name="next-steps"></a>次のステップ

 [Configuration Manager クライアントを使用して管理されているデバイスの構成項目](../../compliance/deploy-use/create-configuration-items.md)