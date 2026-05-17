Build status
============

<table id="status-table">
    <thead>
        <tr>
            <th>Component</th>
            <th>Build status</th>
        </tr>
    </thead>
    <tbody>
    </tbody>
</table>

<script>
    const dansModules = [
        "dans-api-archetype",
        "dans-bagit-lib",
        // "dans-bagpack-lib", // only a stub so far
        "dans-build-resources-maven-plugin",
        "dans-cli-archetype",
        "dans-converter-lib",
        "dans-dataverse-client-lib",
        "dans-dv-upload",
        "dans-java-utils",
        "dans-layer-store-lib",
        "dans-module-archetype",
        "dans-nexus-maven-plugin",
        "dans-ocfl-extensions",
        "dans-ocfl-java-extensions-lib",
        "dans-schema",
        "dans-validation-lib",
        "dd-confirm-archiving",
        "dd-dans-sword2-examples",
        "dd-data-vault",
        "dd-data-vault-api",
        "dd-data-vault-cli",
        "dd-dataverse-authenticator",
        "dd-dataverse-ingest",
        "dd-dataverse-ingest-api",
        "dd-dataverse-ingest-cli",
        "dd-dv-cli",
        "dd-gmh-api",
        "dd-gmh-cli",
        "dd-lob-store",
        "dd-lob-store-api",
        "dd-lob-store-cli",
        "dd-manage-deposit",
        "dd-manage-deposit-api",
        "dd-manage-deposit-cli",
        "dd-parent",
        "dd-register-nbn",
        "dd-sword2",
        "dd-transfer-to-vault",
        "dd-transfer-to-vault-api",
        "dd-transfer-to-vault-cli",
        "dd-validate-bagpack",
        "dd-validate-bagpack-api",
        "dd-validate-bagpack-cli",
        "dd-validate-dans-bag",
        "dd-validate-dans-bag-api",
        "dd-validate-dans-bag-cli",
        "dd-vault-catalog",
        "dd-vault-catalog-api",
        "dd-vault-catalog-cli",
        "dd-vault-ingest",
        "dd-vault-metadata",
        "dd-vault-metadata-api",
        "dd-virus-scan",
        "dd-virus-scan-api"
    ];

    function addModule(modulename, baseUrl = "https://github.com/DANS-KNAW", workflow = "build.yml", badgeName = "Build project") {
        const tableBody = document.querySelector('#status-table tbody');
        const row = document.createElement('tr');

        const nameCell = document.createElement('td');
        nameCell.textContent = modulename;
        row.appendChild(nameCell);

        const statusCell = document.createElement('td');
        const link = document.createElement('a');
        link.href = `${baseUrl}/${modulename}/actions/workflows/${workflow}`;
        link.target = '_blank';
        
        const badge = document.createElement('img');
        badge.src = `${baseUrl}/${modulename}/actions/workflows/${workflow}/badge.svg`;
        badge.alt = badgeName;
        
        link.appendChild(badge);
        statusCell.appendChild(link);
        row.appendChild(statusCell);

        tableBody.appendChild(row);
    }

    function addDansModule(modulename) {
        addModule(modulename);
    }

    document.addEventListener("DOMContentLoaded", function() {
        // Dataverse first
        addModule("dataverse", "https://github.com/IQSS", "maven_unit_test.yml", "Maven Unit Tests");

        // DANS modules sorted
        dansModules.sort().forEach(addDansModule);
    });
</script>
